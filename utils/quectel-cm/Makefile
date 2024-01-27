include $(TOPDIR)/rules.mk

PKG_NAME:=quectel-cm
PKG_VERSION:=1.6.5
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/quectel-cm
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=WWAN
  TITLE:=Qconnect Manager for Quectel WWAN modules
  DEPENDS:=+kmod-usb-net-qmi-wwan-quectel +kmod-usb-serial-option
endef

define Package/quectel-cm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/quectel-CM $(1)/usr/bin/quectel-cm
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/quectel-{mbim,qmi}-proxy $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/lib/netifd/proto
	$(INSTALL_BIN) ./files/quectel.sh $(1)/lib/netifd/proto/

	$(INSTALL_DIR) $(1)/etc/hotplug.d/net
	$(INSTALL_BIN) ./files/smp-affinity-pcie-mhi.sh $(1)/etc/hotplug.d/net/21-smp-affinity-pcie-mhi
	$(INSTALL_BIN) ./files/smp-affinity-qmi-usb.sh $(1)/etc/hotplug.d/net/22-smp-affinity-qmi-usb
endef

$(eval $(call BuildPackage,quectel-cm))
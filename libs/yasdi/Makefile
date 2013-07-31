#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=yasdi
PKG_VERSION:=1.8.1build9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-src.zip
PKG_SOURCE_URL:=http://files.sma.de/dl/11705/
PKG_MD5SUM:=33826860da2ba4fda003e99c7856986b

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

PKG_UNPACK:=unzip -d $(PKG_BUILD_DIR)/ $(DL_DIR)/$(PKG_SOURCE)

CMAKE_INSTALL:=1
PKG_BUILD_PARALLEL:=1

define Package/yasdi/Default
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Library for communication with SMA string inverters
  URL:=http://www.sma-solar.com/
endef

define Package/yasdi/Default/description
  YASDI is an implementation library for communication with
  SMA String Inverters (aka "Sunny Boys"). The name "YASDI" stands for
  "(Y)et (A)nother (S)MA (D)ata (I)mplementation" and means the implementation
  of the communication protocol "SMAData" via "SunnyNet" and "SMANet".

  Functioning as a driver system without its own graphical interface,
  the software implements the communication over serial port and ethernet/UDP
  connections.
endef

define Package/yasdi
  $(call Package/yasdi/Default)
  DEPENDS:=+libpthread
endef

define Package/yasdi/description
  $(call Package/yasdi/Default/description)

  This package contains the main library. You must install at least one
  of the drivers 'serial' or 'ip'.
endef

define Package/yasdi-drv-ip
  $(call Package/yasdi/Default)
  DEPENDS:=yasdi
  TITLE:=IP driver
endef

define Package/yasdi-drv-ip/description
  $(call Package/yasdi/Default/description)

  This package contains the IP (UDP) driver for "SMA Ethernet PiggyBacks".
endef

define Package/yasdi-drv-serial
  $(call Package/yasdi/Default)
  DEPENDS:=yasdi
  TITLE:=Serial driver
endef

define Package/yasdi-drv-serial/description
  $(call Package/yasdi/Default/description)

  This package contains the serial driver.
endef

define Package/yasdishell
  $(call Package/yasdi/Default)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+yasdi
  TITLE:=YASDI shell
endef

define Package/yasdishell/description
  $(call Package/yasdi/Default/description)

  This package contains the yasdi shell utility.
endef

define Package/yasdi/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libyasdi.so.* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libyasdimaster.so.* $(1)/usr/lib/
endef

define Package/yasdi-drv-ip/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*drv_ip*.so.* $(1)/usr/lib/
endef

define Package/yasdi-drv-serial/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*drv_serial*.so.* $(1)/usr/lib/
endef

define Package/yasdishell/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/yasdishell $(1)/usr/bin/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,yasdi))
$(eval $(call BuildPackage,yasdi-drv-ip))
$(eval $(call BuildPackage,yasdi-drv-serial))
$(eval $(call BuildPackage,yasdishell))

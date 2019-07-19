#
# Copyright (C) 2019 Nicolas Thill <nicolas.thill@gmail.com
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pd-comport
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.iem.at/pd/comport.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=0d7cd6a7
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_MAINTAINER:=

PKG_LICENSE:=LGPL-2.1+
PKG_LICENSE_FILES:=LICENSE.txt

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/pd-comport
  SECTION:=sound
  CATEGORY:=Sound
  DEPENDS:=
  TITLE:=PD External for the serial Ports
  URL:=https://git.iem.at/pd/comport
endef

define Package/pd-comport/description
  pd-comport
endef

MAKE_FLAGS += \
	PDINCLUDEDIR="$(STAGING_DIR)/usr/include/libpd" \
	PDLIBDIR="$(STAGING_DIR)/usr/lib" \
	uname="Linux" \
	build.arch="$(HOST_ARCH)" \
	target.arch="$(ARCH)" \
	arch.c.flags="$(TARGET_CFLAGS)" \

MAKE_INSTALL_FLAGS += \
	PDLIBDIR="/usr/lib/pd" \
	uname="Linux" \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/pd
	$(CP) ./files/comport.h $(1)/usr/include/pd/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pd/comport/comport.pd_linux $(1)/usr/lib/libpd-comport.so
endef

define Package/pd-comport/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pd/comport/comport.pd_linux $(1)/usr/lib/libpd-comport.so
endef

$(eval $(call BuildPackage,pd-comport))

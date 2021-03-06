#
# Copyright (C) 2019 Nicolas Thill <nicolas.thill@gmail.com
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libpd
PKG_VERSION:=0.11.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:libpd/libpd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_MAINTAINER:=

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE.txt

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libpd
  SECTION:=sound
  CATEGORY:=Sound
  DEPENDS:=
  TITLE:=Pure Data computer music system as an embeddable audio synthesis library
  URL:=http://libpd.cc/
endef

define Package/libpd/description
  libpd takes the power of one of the world’s most powerful, most
  widely-used environments for making original sound and music
  creations, and lets you put it anywhere.
  It’s free, open source, and can run on a wide variety of devices from
  phones to computers.
endef

MAKE_FLAGS += \
  OPT_CFLAGS="$(TARGET_CFLAGS)" \
  prefix="/usr" \
  UNAME="Linux" \

ifneq ($(CONFIG_LIBPD_SAMPLES),)

SAMPLES:= \
	./samples/c/pdtest/ \
	./samples/c/pdtest_multi/ \
	./samples/c/pdtest_thread/ \
	./samples/cpp/pdtest/ \
	./samples/cpp/pdtest_rtaudio/ \

define Build/Compile/Samples
	( cd $(PKG_BUILD_DIR) ; \
		for sample in $(SAMPLES); do \
			$(MAKE_VARS) $(MAKE) $(MAKE_FLAGS) -C $$$$sample ; \
		done \
	)
endef
Hooks/Compile/Post += Build/Compile/Samples

endif

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libpd $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpd.so $(1)/usr/lib/
endef

define Package/libpd/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpd.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpd))

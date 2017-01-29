#
# Copyright (C) 2017 Venelin Efremov <vefremov@iqury.us>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluezaudio
PKG_VERSION=0.1.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Venelin Efremov <vefremov@iqury.us>
PKG_LICENSE:=Proprietary
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=git@bitbucket.org:ghent360/bluezaudio.git
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=0311d307e25946fec0d567ad981a6c846183b491
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_MD5SUM:=45a7d86d4573ee2b7b4af8ec45543ec0078315e91b4e03555852ea4db3807bef

include $(INCLUDE_DIR)/package.mk

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

define Package/bluezaudio
  SECTION:=sound
  CATEGORY:=Sound
  DEPENDS:= \
    +libstdcpp \
    +libpthread \
    +gflags \
    +glog \
    +dbus \
    +dbuswrapper \
    +bluez5wrapper \
    +libsoxr \
    +fdk-aac \
    +alsa-lib \
    +libgcrypt \
    +liblzo \
    +sbc \
    +libvorbis \
    +espeak
  TITLE:=Dope Bluez 5 audio deamon
  URL:=https://bitbucket.org/ghent360/bluesaudio
endef

define Package/bluezaudio/description
  Dope Bluez 5 audio daemon
endef

define Package/bluezaudio/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/
endef

define Build/Configure
	(cd $(PKG_BUILD_DIR); rm -rf config.{cache,status}; \
		autoreconf -vif \
	);
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	:
endef

$(eval $(call BuildPackage,bluezaudio))

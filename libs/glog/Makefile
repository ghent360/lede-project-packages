#
# Copyright (C) 2017 Venelin Efremov <vefremov@iqury.us>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=glog
PKG_VERSION=0.3.4
PKG_RELEASE:=1
PKG_MAINTAINER:=Venelin Efremov <vefremov@iqury.us>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/google/glog/
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=b6a5e0524c28178985f0d228e9eaa43808dbec3c
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_MD5SUM:=0d55b9b65e31b75de99c61a9ba160f628968806b833ee6e91eaebb8557fb79f2

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += \
    -DBUILD_SHARED_LIBS:BOOL=ON \
    -DBUILD_STATIC_LIBS:BOOL=OFF\

define Package/glog
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libpthread +gflags +libstdcpp
  TITLE:=Google glog library
  URL:=https://github.com/google/glog
endef

define Package/glog/description
  Google glog library
endef

define Package/glog/install	
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/libglog.so.* $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/glog
	$(CP) $(PKG_BUILD_DIR)/glog/*.h $(1)/usr/include/glog
	$(CP) $(PKG_BUILD_DIR)/src/glog/*.h $(1)/usr/include/glog
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/libglog.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,glog))

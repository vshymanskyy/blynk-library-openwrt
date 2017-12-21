include $(TOPDIR)/rules.mk

PKG_NAME:=blynk
PKG_VERSION:=0.5.0
PKG_RELEASE:=1

PKG_MAINTAINER:=Volodymyr Shymanskyy
PKG_LICENSE:=MIT

PKG_BUILD_PARALLEL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/blynkkk/blynk-library.git
PKG_SOURCE_VERSION:=v0.5.0
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

#define Build/Prepare
#	mkdir -p $(PKG_BUILD_DIR)
#	$(CP) -r /data2/Projects/blynk-library-arduino/* $(PKG_BUILD_DIR)/
#endef

define Package/blynk
  SUBMENU:=Blynk
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Blynk App builder for IoT
  URL:=http://www.blynk.cc
  DEPENDS:=+libpthread +librt $(CXX_DEPENDS)
endef

define Package/blynk/description
 Blynk is a platform with iOS and Android apps to control Arduino,
 Raspberry Pi and the likes over the Internet.
 You can easily build graphic interfaces for all your projects
 by simply dragging and dropping widgets.
endef

MAKE_PATH:=linux

MAKE_FLAGS += LD="$(TARGET_CXX)"
#TODO: add -fno-rtti

define Package/blynk/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/linux/blynk $(1)/usr/bin/
endef

$(eval $(call BuildPackage,blynk))

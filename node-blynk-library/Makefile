include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=blynk-library
PKG_NAME:=node-$(PKG_NPM_NAME)
PKG_VERSION:=0.4.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NPM_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://registry.npmjs.org/$(PKG_NPM_NAME)/-/
PKG_MD5SUM:=7e90c28befe0eae9a18b7c6cab966804

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.8.3
PKG_USE_MIPS16:=0

PKG_MAINTAINER:=Volodymyr Shymanskyy
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/node-blynk-library
  DEPENDS:=+node
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Blynk client for Node.js
  URL:=https://www.npmjs.com/package/blynk-library
endef

define Package/node-blynk-library/description
 Blynk is a platform with iOS and Android apps to control Arduino,
 Raspberry Pi and the likes over the Internet.
 You can easily build graphic interfaces for all your projects
 by simply dragging and dropping widgets.
endef

define Build/Prepare
	/bin/tar xzf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR) --strip-components 1
	$(Build/Patch)
endef

CPU:=$(subst powerpc,ppc,$(subst aarch64,arm64,$(subst x86_64,x64,$(subst i386,ia32,$(ARCH)))))

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CPU) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	npm_config_cache=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/npm-cache \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	npm install --build-from-source --target_arch=$(CPU) -g $(PKG_BUILD_DIR)
endef

define Package/node-blynk-library/install
	mkdir -p $(1)/usr/lib/node
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/* $(1)/usr/lib/node/
endef

$(eval $(call BuildPackage,node-blynk-library))


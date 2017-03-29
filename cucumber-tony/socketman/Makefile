#
# How to build socketman a LEDE package 101
#

include $(TOPDIR)/rules.mk

PKG_NAME:=SocketMan
PKG_VERSION:=v1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/cucumber-tony/SocketMan.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=ad6d7a6217c15c4bd9b455a278372f2988a52334
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/socketman
  SECTION:=gopackh
  CATEGORY:=GoPackH
  DEPENDS:=+libcurl +libmosquitto +libnl +libjson-c +zlib
  TITLE:=SocketMan communication package for Cucumber Tony
  URL:=http://www.cucumberwifi.io
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include/libnl3 \
	-DCT_VERSION='\"$(PKG_SOURCE_VERSION)\"' \
	-D__OPENWRT__

define Build/Compile
	CFLAGS="$(TARGET_CPPFLAGS) $(TARGET_CFLAGS)" \
	$(MAKE) $(MAKE_FLAGS) -C $(PKG_BUILD_DIR)/src
endef

define Package/socketman/description
  SocketMan is a light-weight daemon, written purely in C, that runs on most
  OpenWRT, LEDE and other \*nix devices. SocketMan is used at Cucumber Tony to
  control their global estate of access points and routers.
endef

define Package/socketman/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/socketman $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/examples/openwrt/socketman.init $(1)/etc/init.d/socketman
endef

$(eval $(call BuildPackage,socketman))

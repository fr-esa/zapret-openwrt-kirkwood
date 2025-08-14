include $(TOPDIR)/rules.mk

PKG_NAME:=hello-kirkwood
PKG_VERSION:=1.0
PKG_RELEASE:=1
PKG_LICENSE:=MIT
PKG_MAINTAINER:=you <you@example.org>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/hello-kirkwood
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Hello for Kirkwood
endef

define Package/hello-kirkwood/description
 A tiny hello-world program compiled for OpenWrt (kirkwood/arm_xscale).
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

# Компилируем единый .c прямо средствами SDK (без внешнего Makefile)
define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) \
		-o $(PKG_BUILD_DIR)/hello $(PKG_BUILD_DIR)/hello.c \
		$(TARGET_LDFLAGS)
endef

define Package/hello-kirkwood/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hello $(1)/usr/bin/hello
endef

$(eval $(call BuildPackage,hello-kirkwood))

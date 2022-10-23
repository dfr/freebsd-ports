PORTNAME=	buildah
PORTVERSION=	1.28.1.dev
CATEGORIES=	sysutils

MAINTAINER=	dfr@FreeBSD.org
COMMENT=	Manage Pods, Containers and Container Images
WWW=		https://github.com/containers

LICENSE=	GPLv2

LIB_DEPENDS=	libgpgme.so:security/gpgme
RUN_DEPENDS=	containers-common>=0:sysutils/containers-common \
		containernetworking-plugins>=0:net/containernetworking-plugins \
		ocijail:sysutils/ocijail
BUILD_DEPENDS=	go-md2man:textproc/go-md2man \
		bash:shells/bash \
		gsed:textproc/gsed

USES=		gmake go:no_targets pkgconfig

USE_GITHUB=	yes
GH_ACCOUNT=	containers
GH_PROJECT=	buildah
GH_TAGNAME=	c2cf9fa
INSTALL_TARGET=	install install.completions

.include <bsd.port.mk>

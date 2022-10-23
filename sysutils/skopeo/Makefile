PORTNAME=	skopeo
DISTVERSIONPREFIX= v
DISTVERSION=	1.10.0
CATEGORIES=	sysutils

MAINTAINER=	dfr@FreeBSD.org
COMMENT=	Inspect container images and repositories on registries
WWW=		https://github.com/containers

LICENSE=	GPLv2

LIB_DEPENDS=	libgpgme.so:security/gpgme
RUN_DEPENDS=	${LOCALBASE}/etc/containers/containers.conf.sample:sysutils/containers-common
BUILD_DEPENDS=	curl:ftp/curl \
		go-md2man:textproc/go-md2man \
		bash:shells/bash

USES=		gmake pkgconfig go:no_targets
USE_GITHUB=	yes
GH_ACCOUNT=	containers
GH_PROJECT=	skopeo

do-install:
	${GMAKE} -C ${WRKSRC} DESTDIR=${STAGEDIR} GO=${GO_CMD} install-binary
	${GMAKE} -C ${WRKSRC} DESTDIR=${STAGEDIR} GO=${GO_CMD} install-docs
	${GMAKE} -C ${WRKSRC} DESTDIR=${STAGEDIR} GO=${GO_CMD} install-completions
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/containers/registries.d
	${INSTALL_DATA} ${WRKSRC}/default.yaml ${STAGEDIR}${PREFIX}/etc/containers/registries.d/default.yaml

.include <bsd.port.mk>

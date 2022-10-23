PORTNAME=	podman
PORTVERSION=	4.4.0.dev
CATEGORIES=	sysutils

MAINTAINER=	dfr@FreeBSD.org
COMMENT=	Manage Pods, Containers and Container Images
WWW=		https://github.com/containers

LICENSE=	GPLv2

LIB_DEPENDS=	libgpgme.so:security/gpgme
RUN_DEPENDS=	containers-common>=0:sysutils/containers-common \
		containernetworking-plugins>=0:net/containernetworking-plugins \
		conmon:sysutils/conmon \
		ocijail:sysutils/ocijail
BUILD_DEPENDS=	go-md2man:textproc/go-md2man \
		bash:shells/bash \
		gsed:textproc/gsed

USES=		gmake go:no_targets pkgconfig python:3.7+,build shebangfix

SHEBANG_LANG=	python
SHEBANG_FILES=	${WRKSRC}/hack/markdown-preprocess

# Parallel builds are flaky due to some kind of file race in the
# markdown-preprocess phase of the docs build.
MAKE_JOBS_UNSAFE=yes

USE_GITHUB=	yes
GH_ACCOUNT=	containers
GH_PROJECT=	podman
GH_TAGNAME=	d319860

INSTALL_TARGET=	install install.completions

# Temporary until https://github.com/containers/podman/pull/16422 lands
do-install:
	${GMAKE} -C ${WRKSRC} DESTDIR=${STAGEDIR} GO=${GO_CMD} install
	${GMAKE} -C ${WRKSRC} DESTDIR=${STAGEDIR} GO=${GO_CMD} install.completions
	${RM} ${STAGEDIR}${PREFIX}/lib/tmpfiles.d/podman.conf
	${RMDIR} ${STAGEDIR}${PREFIX}/lib/tmpfiles.d

.include <bsd.port.mk>

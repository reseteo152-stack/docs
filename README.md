# GitHub Docs <!-- omit in toc -->

Welcome to GitHub Docs! GitHub’s documentation is open source, meaning anyone from inside or outside the company can contribute. For full contributing guidelines, visit our [contributing guide](https://docs.github.com/en/contributing).


## Quick links by contributor type

* **Hubbers (GitHub employees):** See [CONTRIBUTING.md](https://github.com/github/docs-content/blob/main/CONTRIBUTING.md) in the `docs-content` repository for GitHub-specific processes.

* **Open source contributors:** See [CONTRIBUTING.md](https://github.com/github/docs/blob/main/.github/CONTRIBUTING.md) in the `docs` repository for a quick-start summary.

## How we sync changes across Docs repositories

There are two GitHub Docs repositories: 

- **`github/docs`** (public): Open to external contributions

- **`github/docs-internal`** (private): For GitHub employee contributions. 

The two repositories sync frequently. Content changes in one are reflected in the other.  Hubbers might prefer to post in `docs` when working with a customer, but `docs` has limitations on the types of contributions it accepts to safeguard the site and our workflows. Internal contributions should usually go to `docs-internal`.

**Important:** The `docs` repository accepts contributions to content files (`.md` files in `/content` and select `/data` sections like reusables only). Infrastructure files, workflows, and site-building code are not open for external modification.

## New to contributing

Here are some resources to help you get started with open source contributions:

* [Finding ways to contribute to open source on GitHub](https://docs.github.com/en/get-started/exploring-projects-on-github/finding-ways-to-contribute-to-open-source-on-github)
* [Set up Git](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
* [Collaborating with pull requests](https://docs.github.com/en/github/collaborating-with-pull-requests)

## License

This project is dual-licensed under:

* **Creative Commons Attribution 4.0** - for documentation and content in the assets, content, and data folders (see [LICENSE](LICENSE))
* **MIT License** - for code (see [LICENSE-CODE](LICENSE-CODE))
# Opción A: Ejecución directa con Node (Rápido)
node packages/gemini-cli/dist/index.js

# Opción B: Usando el script del workspace con Debug activado
DEBUG=true npm start --workspace @google/gemini-cli
Mi-Proyecto/ (Raíz)
├── package.json (Configuración global de Workspaces)
└── packages/
    ├── gemini-cli-core/  <-- AQUÍ ESTÁ LA LÓGICA (La carpeta que buscas)
    │   └── src/
    │       └── api/
    │           └── client.ts  <-- AQUÍ PEGAS EL CÓDIGO DEL CLIENTE
    └── gemini-cli/       <-- AQUÍ ESTÁ LA INTERFAZ (Lo que el usuario corre)
cd packages/gemini-cli-core/src/api/
#!/usr/bin/env bash
set -Eeuo pipefail

found() {
        echo "$@"
        exit
}

arch=
if command -v apk > /dev/null && tryArch="$(apk --print-arch)"; then
        arch="$tryArch"
elif command -v dpkg > /dev/null && tryArch="$(dpkg --print-architecture)"; then
        arch="${tryArch##*-}"
elif command -v rpm > /dev/null && tryArch="$(rpm --query --queryformat='%{ARCH}' rpm)"; then
        arch="$tryArch"
elif command -v uname > /dev/null && tryArch="$(uname -m)"; then
        echo >&2 "warning: neither of 'dpkg' or 'apk' found, falling back to 'uname'"
        arch="$tryArch"

        os="$(uname -o 2>/dev/null || :)"
        case "$os" in
                Cygwin | Msys)
                        # TODO support non-amd64 Windows
                        found 'windows-amd64'
                        ;;
        esac
fi

case "$arch" in
        amd64 | x86_64)    found 'amd64'    ;;
        arm64 | aarch64)   found 'arm64v8'  ;;
        armel)             found 'arm32v5'  ;;
        armv6*)            found 'arm32v6'  ;;
        armv7*)            found 'arm32v7'  ;;
        i[3456]86 | x86)   found 'i386'     ;;
        mips64el)          found 'mips64le' ;; # TODO "uname -m" is just "mips64" (which is also "apk --print-arch" on big-endian MIPS) so we ought to disambiguate that somehow
        ppc64el | ppc64le) found 'ppc64le'  ;;
        riscv64)           found 'riscv64'  ;;
        s390x)             found 's390x'    ;;

        armhf)
                if [ -s /etc/os-release ] && id="$(grep -Em1 '^ID=[^[:space:]]+$' /etc/os-release)"; then
                        eval "$id"
                        case "${ID:-}" in
                                alpine | raspbian) found 'arm32v6' ;;
                                *)                 found 'arm32v7' ;;
                        esac
                else
                        echo >&2 "warning: '$arch' is ambiguous (and '/etc/os-release' is missing 'ID=xxx'), assuming 'arm32v6' for safety"
                        found 'arm32v6'
                fi
                ;;

        *)
                echo >&2 "error: unknown architecture: '$arch'"
                exit 1
                ;;
esac12c758028e6c68bc4780aec4bb902e619e9220416c47dbbb89c2665758a08e580424c128f5f423davendor/golang.org/x/crypto/cryptobyte/asn1
 vendor/golang.org/x/crypto/internal/alias
 google.golang.org/protobuf/internal/flags
 google.golang.org/protobuf/internal/set
 google.golang.org/grpc/attributes
 google.golang.org/grpc/serviceconfig
 github.com/containerd/containerd/defaults
 github.com/containerd/containerd/services
 image/color
 github.com/ProtonMail/go-crypto/internal/byteutil
 golang.org/x/crypto/cryptobyte/asn1
 github.com/pjbgf/sha1cd/internal
 github.com/pjbgf/sha1cd/ubc
 github.com/go-git/go-git/v5/plumbing/color
 github.com/golang/groupcache/lru
 golang.org/x/crypto/internal/alias
 internal/race
 internal/sync
 internal/runtime/maps
 github.com/klauspost/compress
 runtime
 iter
 internal/reflectlite
 github.com/containerd/containerd/version
 crypto/internal/fips140/subtle
 weak
 sync
 maps
 slices
 crypto/subtle
 sort
 errors
 internal/bisect
 internal/testlog
 google.golang.org/protobuf/internal/pragma
 internal/singleflight
 google.golang.org/grpc/internal/buffer
 unique
 google.golang.org/grpc/internal/grpcsync
 internal/oserror
 io
 strconv
 path
 math/rand/v2
 syscall
 vendor/golang.org/x/net/dns/dnsmessage
 internal/godebug
 github.com/moby/locker
 bytes
 strings
 hash
 crypto/internal/randutil
 hash/crc32
 github.com/gogo/protobuf/sortkeys
 crypto/internal/fips140deps/godebug
 math/rand
 internal/saferio
 hash/fnv
 hash/adler32
 crypto
 reflect
 net/netip
 crypto/internal/fips140
 html
 bufio
 crypto/internal/fips140/sha256
 crypto/internal/fips140/sha3
 crypto/internal/fips140/sha512
 regexp/syntax
 crypto/internal/impl
 crypto/tls/internal/fips140tls
 vendor/golang.org/x/text/transform
 net/http/internal/ascii
 golang.org/x/text/transform
 crypto/internal/fips140/hmac
 time
 internal/syscall/unix
 crypto/internal/fips140/check
 internal/syscall/execenv
 crypto/internal/fips140/aes
 crypto/internal/fips140/edwards25519/field
 crypto/internal/fips140/nistec/fiat
 crypto/internal/fips140/bigmod
 crypto/sha3
crypto/internal/fips140/edwards25519
 crypto/internal/fips140hash
 crypto/internal/fips140/hkdf
 crypto/internal/fips140/tls12
 crypto/internal/fips140/tls13
 regexp
 github.com/docker-library/bashbrew/pkg/stripper
 golang.org/x/crypto/openpgp/errors
 compress/bzip2
 golang.org/x/crypto/cast5
 golang.org/x/crypto/openpgp/s2k
 image
 pault.ag/go/topsort
 github.com/docker-library/bashbrew/pkg/dockerfile
 container/heap
 github.com/cloudflare/circl/sign
 github.com/cloudflare/circl/internal/sha3
 crypto/fips140
 golang.org/x/crypto/blowfish
 context
 io/fs
 internal/poll
 google.golang.org/grpc/backoff
 google.golang.org/grpc/internal/grpcrand
 google.golang.org/grpc/keepalive
 google.golang.org/grpc/tap
 golang.org/x/sync/semaphore
 github.com/containerd/containerd/gc
 image/internal/imageutil
 github.com/go-git/go-git/v5/internal/url
 image/jpeg
 golang.org/x/net/context
 google.golang.org/grpc/internal/backoff
 github.com/jbenet/go-context/io
 internal/filepathlite
 embed
 github.com/go-git/go-git/v5/utils/ioutil
 google.golang.org/protobuf/internal/editiondefaults
 os
 internal/fmtsort
 encoding/binary
 crypto/internal/fips140/nistec
 encoding/base64
 github.com/klauspost/compress/internal/le
 golang.org/x/sys/unix
 github.com/klauspost/compress/internal/snapref
 vendor/golang.org/x/crypto/internal/poly1305
 github.com/klauspost/compress/zstd/internal/xxhash
 golang.org/x/crypto/blake2b
 encoding/pem
 golang.org/x/crypto/openpgp/armor
 golang.org/x/crypto/internal/poly1305
 golang.org/x/crypto/argon2
 crypto/internal/sysrand
 io/ioutil
 path/filepath
 google.golang.org/protobuf/internal/detrand
 fmt
 net
 crypto/internal/entropy
 google.golang.org/grpc/internal/envconfig
 crypto/internal/fips140/drbg
 os/signal
 pault.ag/go/debian/internal
 os/exec
 golang.org/x/sys/cpu
 github.com/go-git/go-billy/v5
 crypto/internal/fips140/aes/gcm
 crypto/internal/fips140only
 crypto/internal/fips140/ed25519
 crypto/internal/fips140/mlkem
 crypto/internal/fips140/ecdh
 crypto/cipher
 crypto/internal/fips140/ecdsa
 crypto/md5
 encoding/hex
encoding/json
 os/user
 crypto/internal/boring
 log
 compress/flate
 net/url
 crypto/sha256
 crypto/sha512
 archive/tar
 text/template/parse
 golang.org/x/net/internal/timeseries
 math/big
 compress/gzip
 crypto/aes
 crypto/des
 crypto/ecdh
 crypto/hmac
 text/template
 vendor/golang.org/x/crypto/chacha20
 crypto/rc4
 crypto/internal/fips140/rsa
 crypto/sha1
 vendor/golang.org/x/crypto/chacha20poly1305
 vendor/golang.org/x/text/unicode/bidi
 vendor/golang.org/x/text/unicode/norm
 github.com/gogo/protobuf/proto
 vendor/golang.org/x/net/http2/hpack
 vendor/golang.org/x/text/secure/bidirule
 mime
 mime/quotedprintable
 net/http/internal
 text/tabwriter
 google.golang.org/grpc/internal/grpclog
 google.golang.org/protobuf/internal/errors
 google.golang.org/grpc/grpclog
 google.golang.org/protobuf/encoding/protowire
 net/textproto
 html/template
 google.golang.org/protobuf/reflect/protoreflect
 crypto/rand
 crypto /elliptic
 crypto/internal/boring/bbig
 encoding/asn1
 crypto/ed25519
 crypto/internal/hpke
 crypto/rsa
 crypto/dsa
 vendor/golang.org/x/net/idna
 mime/multipart
 google.golang.org/grpc/connectivity
 go/token
 google.golang.org/protobuf/internal/version
 google.golang.org/grpc/metadata
 google.golang.org/grpc/codes
 golang.org/x/text/unicode/bidi
 golang.org/x/text/unicode/norm
 golang.org/x/net/http2/hpack
 proveedor/golang.org/x/net/http/httpguts
 proveedor/golang.org/x/crypto/cryptobyte
 crypto/x509/pkix
 proveedor/golang.org/x/net/http/httpproxy
 google.golang.org/protobuf/internal/encoding/messageset
 google.golang.org/protobuf/internal/strs
 google.golang.org/protobuf/internal/genid
 google.golang.org/protobuf/internal/order
 google.golang.org/protobuf/internal/encoding/text
 google.golang.org/protobuf/reflect/protoregistry
 google.golang.org/protobuf/runtime/protoiface
 google.golang.org/protobuf/internal/descfmt
 google.golang.org/protobuf/internal/descopts
 crypto/ecdsa
 google.golang.org/protobuf/internal/encoding/json
 google.golang.org/protobuf/proto
 google.golang.org/grpc/internal/grpcutil
 google.golang.org/grpc/encoding
google.golang.org/grpc/internal/balancerload
 golang.org/x/text/secure/bidirule
 google.golang.org/grpc/internal/syscall
 google.golang.org/grpc/stats
 google.golang.org/protobuf/internal/encoding/defval
 github.com/opencontainers/go-digest
 github.com/pkg/errors
 github.com/sirupsen/logrus
 github.com/containerd/containerd/pkg/userns
 github.com/containerd/continuity/sysx
 golang.org/x/sync/errgroup
 github.com/klauspost/compress/fse
 crypto/x509
 runtime/debug
 golang.org/x/net/idna
 golang.org/x/sys/execabs
 google.golang.org/protobuf/encoding/prototext
 google.golang.org/protobuf/internal/filedesc
 github.com/containerd/fifo
 github.com/klauspost/compress/huff0
 github.com/containerd/containerd/log
 github.com/containerd/continuity/fs
 github.com/containerd/containerd/cio
 golang.org/x/net/http/httpguts
 github.com/opencontainers/image-spec/specs-go
 github.com/opencontainers/image-spec/specs-go/v1
 github.com/moby/sys/mountinfo
 github.com/containerd/containerd/reference
 github.com/klauspost/compress/zstd
 github.com/containerd/containerd/reference/docker
 github.com/containerd/containerd/leases
 github.com/containerd/containerd/mount
 github.com/containerd/containerd/pkg/cap
 github.com/containerd/containerd/archive
 github.com/opencontainers/runc/libcontainer/user
 github.com/opencontainers/runtime-spec/specs-go
 github.com/containerd/containerd/pkg/dialer
 github.com/containerd/containerd/pkg/kmutex
 crypto/tls
 github.com/docker/go-events
 github.com/containerd/containerd/snapshots
 github.com/opencontainers/image-spec/identity
 database/sql/driver
 github.com/moby/sys/signal
 github.com/opencontainers/selinux/pkg/pwalkdir
 github.com/opencontainers/selinux/go-selinux
 go.etcd.io/bbolt
 compress/zlib
 github.com/google/uuid
 google.golang.org/protobuf/internal/encoding/tag
 google.golang.org/protobuf/encoding/protojson
 github.com/gogo/protobuf/types
 google.golang.org/protobuf/internal/impl
 github.com/containerd/containerd/runtime/linux/runctypes
 github.com/containerd/containerd/runtime/v2/runc/options
 github.com/opencontainers/selinux/go-selinux/label
 golang.org/x/crypto/openpgp/elgamal
 pault.ag/go/debian/version
 golang.org/x/crypto/openpgp/packet
 pault.ag/go/debian/dependency
 pault.ag/go/debian/hashio
github.com/docker-library/bashbrew/pkg/execpipe
 dario.cat/mergo
 github.com/ProtonMail/go-crypto/openpgp/errors
 github.com/ProtonMail/go-crypto/openpgp/armor
 github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
 github.com/ProtonMail/go-crypto/eax
 github.com/ProtonMail/go-crypto/ocb
 github.com/ProtonMail/go-crypto/bitcurves
 github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
 github.com/ProtonMail/go-crypto/brainpool
 github.com/ProtonMail/go-crypto/openpgp/internal/encoding
 golang.org/x/crypto/cryptobyte
 github.com/cloudflare/circl/math
 github.com/ProtonMail/go-crypto/openpgp/elgamal
 github.com/ProtonMail/go-crypto/openpgp/s2k
 golang.org/x/crypto/hkdf
 github.com/containerd/containerd/archive/compression
 golang.org/x/crypto/sha3
 golang.org/x/crypto/openpgp
 golang.org/x/crypto/openpgp/clearsign
 github.com/cyphar/filepath-securejoin
 github.com/cloudflare/circl/internal/conv
 github.com/go-git/go-billy/v5/helper/polyfill
 github.com/go-git/go-billy/v5/util
 github.com/cloudflare/circl/math/fp25519
 github.com/cloudflare/circl/math/fp448
 github.com/cloudflare/circl/math/mlsbset
 pault.ag/go/debian/control
 github.com/go-git/go-billy/v5/helper/chroot
 github.com/cloudflare/circl/dh/x448
 github.com/cloudflare/circl/dh/x25519
 github.com/cloudflare/circl/sign/ed25519
 github.com/cloudflare/circl/ecc/goldilocks
 github.com/ProtonMail/go-crypto/openpgp/x25519
 github.com/ProtonMail/go-crypto/openpgp/x448
 github.com/go-git/go-billy/v5/osfs
 github.com/pjbgf/sha1cd
 encoding/gob
 github.com/ProtonMail/go-crypto/openpgp/ed25519
 github.com/go-git/go-git/v5/plumbing/hash
 github.com/containerd/containerd/api/types
 github.com/containerd/typeurl
 github.com/gogo/googleapis/google/rpc
 net/http/httptrace
 google.golang.org/grpc/internal/credentials
 net/http
 golang.org/x/net/internal/httpcommon
 github.com/containerd/containerd/api/types/task
 github.com/containerd/containerd/containers
 github.com/containerd/containerd/events
 github.com/containerd/containerd/metadata/boltutil
 github.com/cloudflare/circl/sign/ed448
 github.com/go-git/go-git/v5/plumbing
 github.com/go-git/gcfg/token
 github.com/go-git/gcfg/types
 github.com/ProtonMail/go-crypto/openpgp/internal/ecc
 github.com/ProtonMail/go-crypto/openpgp/ed448
 github.com/go-git/gcfg/scanner
gopkg.in/warnings.v0
 github.com/go-git/go-git/v5/internal/path_util
 github.com/go-git/go-git/v5/internal/revision
 github.com/ProtonMail/go-crypto/openpgp/ecdh
 github.com/ProtonMail/go-crypto/openpgp/ecdsa
 github.com/ProtonMail/go-crypto/openpgp/eddsa
 github.com/go-git/go-git/v5/plumbing/cache
 github.com/go-git/go-git/v5/plumbing/filemode
 github.com/ProtonMail/go-crypto/openpgp/packet
 github.com/go-git/go-git/v5/utils/binary
 github.com/go-git/go-git/v5/utils/sync
 github.com/emirpasic/gods/utils
 github.com/go-git/go-git/v5/plumbing/format/index
 github.com/go-git/go-git/v5/plumbing/format/idxfile
 github.com/emirpasic/gods/containers
 github.com/go-git/go-git/v5/plumbing/format/diff
 github.com/go-git/go-git/v5/plumbing/storer
 github.com/emirpasic/gods/lists
 github.com/emirpasic/gods/trees
 github.com/emirpasic/gods/lists/arraylist
 github.com/go-git/gcfg
 github.com/go-git/go-git/v5/plumbing/format/packfile
 github.com/sergi/go-diff/diffmatchpatch
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 github.com/emirpasic/gods/trees/binaryheap
 github.com/go-git/go-git/v5/utils/merkletrie
 github.com/go-git/go-git/v5/plumbing/format/config
 github.com/go-git/go-git/v5/utils/trace
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 google.golang.org/protobuf/internal/filetype
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 github.com/go-git/go-git/v5/utils/diff
 google.golang.org/protobuf/runtime/protoimpl
 github.com/kevinburke/ssh_config
 crypto/mlkem
 golang.org/x/crypto/chacha20
 golang.org/x/crypto/curve25519
 google.golang.org/protobuf/types/descriptorpb
 google.golang.org/protobuf/types/known/anypb
 google.golang.org/protobuf/types/known/durationpb
 google.golang.org/protobuf/types/known/timestamppb
 github.com/golang/protobuf/ptypes/duration
 github.com/go-git/go-git/v5/storage
 github.com/golang/protobuf/ptypes/any
 google.golang.org/genproto/googleapis/rpc/status
 github.com/golang/protobuf/ptypes/timestamp
 github.com/go-git/go-git/v5/storage/memory
 github.com/go-git/go-git/v5/plumbing/format/objfile
 github.com/ProtonMail/go-crypto/openpgp
golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 golang.org/x/net/internal/socks
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 golang.org/x/crypto/ssh
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 github.com/go-git/go-git/v5/utils/merkletrie/index
 golang.org/x/net/proxy
 github.com/docker-library/bashbrew/pkg/tarscrub
 github.com/docker-library/bashbrew/pkg/templatelib
 flag
 github.com/russross/blackfriday/v2
 google.golang.org/protobuf/types/gofeaturespb
 github.com/go-git/go-git/v5/storage/filesystem
 github.com/go-git/go-git/v5/plumbing/object
 github.com/go-git/go-git/v5/plumbing/transport
 google.golang.org/protobuf/reflect/protodesc
 golang.org/x/term
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 github.com/go-git/go-git/v5/plumbing/transport/git
 github.com/cpuguy83/go-md2man/v2/md2man
 github.com/urfave/cli
 github.com/golang/protobuf/proto
 github.com/go-git/go-git/v5/plumbing/revlist
 github.com/go-git/go-git/v5/plumbing/transport/server
 github.com/go-git/go-git/v5/plumbing/transport/file
 golang.org/x/crypto/ssh/agent
 golang.org/x/crypto/ssh/knownhosts
 google.golang.org/grpc/credentials
 github.com/golang/protobuf/jsonpb
 google.golang.org/grpc/encoding/proto
 github.com/golang/protobuf/ptypes
 google.golang.org/grpc/binarylog/grpc_binarylog_v1
 github.com/skeema/knownhosts
 github.com/xanzy/ssh-agent
 github.com/go-git/go-git/v5/plumbing/transport/ssh
 google.golang.org/grpc/credentials/insecure
 google.golang.org/grpc/internal/channelz
 google.golang.org/grpc/internal/status
 google.golang.org/grpc/peer
 google.golang.org/grpc/internal/pretty
 google.golang.org/grpc/status
 google.golang.org/grpc/resolver
 github.com/containerd/containerd/errdefs
 github.com/containerd/ttrpc
 google.golang.org/grpc/internal/binarylog
 google.golang.org/grpc/internal
 google.golang.org/grpc/internal/metadata
 google.golang.org/grpc/balancer/grpclb/state
 google.golang.org/grpc/internal/resolver/passthrough
 google.golang.org/grpc/internal/transport/networktype
 google.golang.org/grpc/internal/resolver/dns
 github.com/containerd/containerd/filters
 github.com/containerd/containerd/labels
 google.golang.org/grpc/internal/resolver/unix
 github.com/containerd/containerd/platforms
github.com/containerd/containerd/identifiers
 google.golang.org/grpc/channelz
 google.golang.org/grpc/balancer
 google.golang.org/grpc/internal/serviceconfig
 google.golang.org/grpc/balancer/base
 github.com/containerd/containerd/content
 google.golang.org/grpc/internal/resolver
 github.com/docker-library/bashbrew/architecture
 github.com/containerd/containerd/namespaces
 google.golang.org/grpc/balancer/roundrobin
 google.golang.org/grpc/internal/balancer/gracefulswitch
 github.com/containerd/containerd/images
 github.com/containerd/containerd/content/local
 golang.org/x/net/http2
 net/http/httputil
 github.com/containerd/containerd/remotes/errors
 golang.org/x/net/trace
 github.com/containerd/containerd/events/exchange
 golang.org/x/net/context/ctxhttp
 github.com/docker-library/bashbrew/manifest
 github.com/containerd/containerd/remotes/docker/auth
 github.com/containerd/containerd/plugin
 github.com/go-git/go-git/v5/plumbing/transport/http
 github.com/containerd/containerd/diff
 github.com/containerd/containerd/images/archive
 github.com/containerd/containerd/oci
 github.com/containerd/containerd/remotes
 github.com/containerd/containerd/rootfs
 github.com/containerd/containerd/metadata
 github.com/go-git/go-git/v5/plumbing/transport/client
 github.com/containerd/containerd/remotes/docker/schema1
 github.com/go-git/go-git/v5
 github.com/containerd/containerd/remotes/docker
 github.com/docker-library/bashbrew/registry
 google.golang.org/grpc/internal/transport
 github.com/docker-library/bashbrew/pkg/gitfs
 google.golang.org/grpc
 github.com/containerd/containerd/api/services/containers/v1
 github.com/containerd/containerd/api/services/content/v1
 github.com/containerd/containerd/api/services/diff/v1
 github.com/containerd/containerd/api/services/events/v1
 github.com/containerd/containerd/api/services/images/v1
 github.com/containerd/containerd/api/services/introspection/v1
 github.com/containerd/containerd/api/services/leases/v1
 github.com/containerd/containerd/api/services/namespaces/v1
 github.com/containerd/containerd/api/services/snapshots/v1
 github.com/containerd/containerd/api/services/tasks/v1
 github.com/containerd/containerd/api/services/version/v1
 github.com/containerd/containerd/leases/proxy
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/services/introspection
github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-i386
 -rwxr-xr-x 1 root root 20M Mar 14 00:58 bin/bashbrew-i386*
 + file bin/bashbrew-i386
 bin/bashbrew-i386: ELF 32-bit LSB executable, Intel i386, version 1 (SYSV), statically linked, BuildID[sha1]=22c71ac96ada8579d3d2e427c665db5181c3c101, stripped
 + for bashbrewArch en $BASHBREW_ARCHES
 ++ bashbrew-arch-to-goenv.sh mips64le
 + goEnv='export GOARCH=mips64le GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 + eval 'export GOARCH=mips64le GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 ++ export GOARCH=mips64le GOOS=linux
 ++ GOARCH=mips64le
 ++ GOOS=linux
 ++ unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64
 + '[' linux = windows ']'
 + ext=
 + LDFLAGS='-s -w'
 + case "$GOOS" in
 + LDFLAGS+=' -d'
 + targetBin=bin/bashbrew-mips64le
 + go build -v -ldflags '-s -w -d' -tags netgo -installsuffix netgo -o bin/bashbrew-mips64le ./cmd/bashbrew
 internal/goarch
 internal/byteorder
 internal/unsafeheader
 internal/goos
 internal/coverage/rtcov
 internal/godebugs
 internal/cpu
 internal/profilerecord
 internal/runtime/atomic
 internal/goexperiment
 internal/abi
 internal/chacha8rand
 internal/asan
 internal/msan
 internal/runtime/math
 internal/runtime/sys
 internal/runtime/syscall
 sync/atomic
 math/bits
 internal/bytealg
 unicode
 unicode/utf8
 internal/stringslite
 internal/runtime/exithook
 internal/itoa
 math
 crypto/internal/fips140/alias
 crypto/internal/fips140deps/byteorder
 crypto/internal/fips140deps/cpu
 cmp
 crypto/internal/boring/sig
 encoding
 unicode/utf16
 log/internal
 internal/nettrace
 container/list
 vendor/golang.org/x/crypto/cryptobyte/asn1
 vendor/golang.org/x/crypto/internal/alias
 google.golang.org/protobuf/internal/flags
 google.golang.org/protobuf/internal/set
 google.golang.org/grpc/attributes
 google.golang.org/grpc/serviceconfig
 github.com/containerd/containerd/defaults
 github.com/containerd/containerd/services
 image/color
github.com/ProtonMail/go-crypto/internal/byteutil
 golang.org/x/crypto/cryptobyte/asn1
 github.com/pjbgf/sha1cd/internal github.com/pjbgf/sha1cd/ubc
 github.com/go-git/go-git/v5/plumbing/color
 github.com/golang/groupcache/lru
 golang.org/x/crypto/internal/alias
 github.com/klauspost/compress
 internal
 /race
 internal/runtime/maps
 internal/sync
 runtime
 internal/reflectlite
 sync
 iter
 crypto/internal/fips140/subtle
 weak
 github.com/containerd/containerd/version
 slices
 maps
 crypto/subtle
 internal/bisect
 internal/singleflight
 internal/testlog
 google.golang.org/protobuf/internal/pragma
 google.golang.org/grpc/internal/buffer
 google.golang.org/grpc/internal/grpcsync
 unique
 internal/godebug
 sort
 errors
 internal/oserror
 io
 math/rand/v2
 path
 strconv
 syscall
 vendor/golang.org/x/net/dns/dnsmessage
 github.com/moby/locker
 golang.org/x/crypto/cast5
 pault.ag/go/topsort
 bytes
 strings
 hash
 crypto/internal/randutil
 crypto/internal/fips140deps/godebug
 github.com/gogo/protobuf/sortkeys
 hash/crc32
 math/rand
 internal/saferio
 hash/fnv
 crypto/internal/fips140
 html
 crypto
 reflect
 regexp/syntax
 net/netip
 bufio
 crypto/internal/fips140/sha256
 crypto/internal/fips140/sha3
 crypto/internal/fips140/sha512
 crypto/tls/internal/fips140tls
 vendor/golang.org/x/text/transform
 crypto/sha3
 net/http/internal/ascii
 crypto/internal/fips140/hmac
 golang.org/x/text/transform
 github.com/docker-library/bashbrew/pkg/stripper
 crypto/internal/fips140/check
 crypto/internal/fips140hash
 golang.org/x/crypto/openpgp/errors
 crypto/internal/fips140/aes
 crypto/internal/fips140/nistec/fiat
 crypto/internal/fips140/edwards25519/field
 crypto/internal/fips140/bigmod
 time
 internal/syscall/unix
 internal/syscall/execenv
 crypto/internal/fips140/edwards25519
 crypto/internal/fips140/hkdf
 regexp
 crypto/internal/fips140/tls12
 crypto/internal/fips140/tls13
 compress/bzip2
 hash/adler32
 golang.org/x/crypto/openpgp/s2k
imagen
 github.com/docker-library/bashbrew/pkg/dockerfile
 contenedor/heap
 github.com/cloudflare/circl/sign
 crypto/fips140
 github.com/go-git/go-git/v5/internal/url
 golang.org/x/crypto/blowfish
 imagen/internal/imageutil
 imagen/jpeg
 contexto
 io/fs
 internal/poll
 google.golang.org/grpc/backoff
 google.golang.org/grpc/internal/grpcrand
 crypto/internal/fips140/nistec
 google.golang.org/grpc/keepalive
 google.golang.org/grpc/internal/backoff
 google.golang.org/grpc/tap
 golang.org/x/sync/semaphore
 github.com/containerd/containerd/gc
 golang.org/x/net/context
 internal/filepathlite
 embed
 github.com/jbenet/go-context/io
 github.com/go-git/go-git/v5/utils/ioutil
 google.golang.org/protobuf/internal/editiondefaults
 os
 encoding/binary
 internal/fmtsort
 encoding/base64
 vendor/golang.org/x/crypto/internal/poly1305
 golang.org/x/sys/unix
 github.com/klauspost/compress/internal/le
 github.com/klauspost/compress/internal/snapref
 github.com/klauspost/compress/zstd/internal/xxhash
 github.com/cloudflare/circl/internal/sha3
 golang.org/x/crypto/blake2b
 golang.org/x/crypto/internal/poly1305
 golang.org/x/crypto/argon2
 golang.org/x/crypto/openpgp/armor
 encoding/pem
 crypto/internal/sysrand
 fmt
 path/filepath
 io/ioutil
 google.golang.org/protobuf/internal/detrand
 net
 google.golang.org/grpc/internal/envconfig
 os/signal
 pault.ag/go/debian/internal
 golang.org/x/sys/cpu
 golang.org/x/crypto/sha3
 crypto/internal/entropy
 crypto/internal/fips140/drbg
 github.com/go-git/go-billy/v5
 crypto/internal/fips140only
 crypto/internal/fips140/ecdsa
 crypto/internal/fips140/aes/gcm
 crypto/internal/fips140/ecdh
 crypto/internal/fips140/ed25519
 crypto/internal/fips140/mlkem
 crypto/md5
 crypto/rc4
 crypto/internal/fips140/rsa
 crypto/cipher
 os/exec
 github.com/go-git/go-billy/v5/helper/polyfill
 github.com/go-git/go-billy/v5/util
 github.com/go-git/go-billy/v5/helper/chroot
 crypto/internal/boring
 crypto/des
 encoding/hex
 encoding/json
 crypto/sha256
 crypto/sha512
 os/user
 log
 compress/flate
 net/url
text/template/parse
 archive/tar
 golang.org/x/net/internal/timeseries
 compress/gzip
 math/big
 crypto/aes
 crypto/ecdh
 crypto/hmac
 text/template
 vendor/golang.org/x/crypto/chacha20
 crypto/sha1
 vendor/golang.org/x/text/unicode/bidi
 vendor/golang.org/x/crypto/chacha20poly1305
 vendor/golang.org/x/text/unicode/norm
 github.com/gogo/protobuf/proto
 vendor/golang.org/x/text/secure/bidirule
 vendor/golang.org/x/net/http2/hpack
 mime
 mime/quotedprintable
 net/http/internal
 text/tabwriter
 google.golang.org/grpc/internal/grpclog
 net/textproto
 html/template
 google.golang.org/protobuf/internal/errors
 google.golang.org/grpc/grpclog
 google.golang.org/protobuf/encoding/protowire
 vendor/golang.org/x/net/idna
 google.golang.org/grpc/connectivity
 google.golang.org/protobuf/reflect/protoreflect
 go/token
 google.golang.org/protobuf/internal/version
 google.golang.org/grpc/metadata
 google.golang.org/grpc/codes
 golang.org/x/text/unicode/bidi
 google.golang.org/grpc/internal/grpcutil
 google.golang.org/grpc/encoding
 crypto/rand
 crypto/elliptic
 crypto/internal/boring/bbig
 encoding/asn1
 crypto/ed25519
 crypto/internal/hpke
 crypto/rsa
 crypto/dsa
 mime/multipart
 google.golang.org/grpc/internal/balancerload
 proveedor/golang.org/x/net/http/httpguts
 proveedor/golang.org/x/crypto/cryptobyte
 crypto/x509/pkix
 proveedor/golang.org/x/net/http/httpproxy
 golang.org/x/text/secure/bidirule
 golang.org/x/text/unicode/norm
 golang.org/x/net/http2/hpack
 google.golang.org/protobuf/internal/encoding/messageset
 google.golang.org/protobuf/internal/strs
 google.golang.org/protobuf/internal/genid
 google.golang.org/protobuf/internal/order
 google.golang.org/protobuf/reflect/protoregistry
 google.golang.org/protobuf/internal/encoding/text
 google.golang.org/protobuf/runtime/protoiface
 google.golang.org/protobuf/internal/descfmt
 crypto/ecdsa
 google.golang.org/protobuf/internal/descopts
 google.golang.org/protobuf/internal/encoding/json
 google.golang.org/grpc/internal/syscall
 google.golang.org/grpc/stats
 google.golang.org/protobuf/proto
 github.com/opencontainers/go-digest
 github.com/pkg/errors
 github.com/sirupsen/logrus
google.golang.org/protobuf/internal/encoding/defval
 github.com/containerd/containerd/pkg/userns
 github.com/containerd/continuity/sysx
 golang.org/x/sync/errgroup
 github.com/klauspost/compress/fse
 runtime/debug
 golang.org/x/sys/execabs
 github.com/containerd/fifo
 github.com/klauspost/compress/huff0
 crypto/x509
 google.golang.org/protobuf/encoding/prototext
 google.golang.org/protobuf/internal/filedesc
 golang.org/x/net/idna
 github.com/containerd/containerd/cio
 github.com/containerd/containerd/log
 github.com/containerd/continuity/fs
 github.com/opencontainers/image-spec/specs-go
 github.com/moby/sys/mountinfo
 github.com/opencontainers/image-spec/specs-go/v1
 github.com/containerd/containerd/reference
 github.com/containerd/containerd/reference/docker
 github.com/klauspost/compress/zstd
 github.com/containerd/containerd/mount
 github.com/containerd/containerd/archive
 github.com/containerd/containerd/leases
 github.com/containerd/containerd/pkg/cap
 github.com/opencontainers/runc/libcontainer/user
 github.com/containerd/containerd/snapshots
 golang.org/x/net/http/httpguts
 github.com/opencontainers/runtime-spec/specs-go
 github.com/containerd/containerd/pkg/dialer
 github.com/containerd/containerd/pkg/kmutex
 github.com/docker/go-events
 google.golang.org/protobuf/internal/encoding/tag
 google.golang.org/protobuf/encoding/protojson
 github.com/opencontainers/image-spec/identity
 database/sql/driver
 github.com/moby/sys/signal
 github.com/opencontainers/selinux/pkg/pwalkdir
 google.golang.org/protobuf/internal/impl
 go.etcd.io/bbolt
 github.com/opencontainers/selinux/go-selinux
 github.com/gogo/protobuf/types
 github.com/containerd/containerd/runtime/linux/runctypes
 crypto/tls
 github.com/containerd/containerd/runtime/v2/runc/options
 github.com/google/uuid
 github.com/opencontainers/selinux/go-selinux/label
 compress/zlib
 golang.org/x/crypto/openpgp/elgamal
 pault.ag/go/debian/version
 pault.ag/go/debian/hashio
 pault.ag/go/debian/dependency
 github.com/docker-library/bashbrew/pkg/execpipe
 golang.org/x/crypto/openpgp/packet
 dario.cat/mergo
 github.com/ProtonMail/go-crypto/openpgp/errors
 github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
 github.com/ProtonMail/go-crypto/openpgp/armor
 github.com/ProtonMail/go-crypto/eax
github.com/ProtonMail/go-crypto/ocb
 github.com/ProtonMail/go-crypto/bitcurves
 github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
 github.com/ProtonMail/go-crypto/brainpool
 github.com/ProtonMail/go-crypto/openpgp/internal/encoding
 golang.org/x/crypto/cryptobyte
 github.com/cloudflare/circl/math
 github.com/ProtonMail/go-crypto/openpgp/elgamal
 github.com/ProtonMail/go-crypto/openpgp/s2k
 github.com/containerd/containerd/archive/compression
 golang.org/x/crypto/hkdf
 github.com/cyphar/filepath-securejoin
 github.com/pjbgf/sha1cd
 github.com/cloudflare/circl/internal/conv
 encoding/gob
 github.com/go-git/go-git/v5/plumbing/hash
 github.com/cloudflare/circl/math/fp25519
 github.com/cloudflare/circl/math/fp448
 golang.org/x/crypto/openpgp
 golang.org/x/crypto/openpgp/clearsign
 github.com/cloudflare/circl/dh/x25519
 github.com/cloudflare/circl/dh/x448
 github.com/cloudflare/circl/sign/ed25519
 github.com/cloudflare/circl/math/mlsbset
 github.com/containerd/containerd/api/types
 github.com/containerd/typeurl
 github.com/gogo/googleapis/google/rpc
 github.com/containerd/containerd/api/types/task
 github.com/containerd/containerd/containers
 github.com/containerd/containerd/events
 github.com/containerd/containerd/metadata/boltutil
 pault.ag/go/debian/control
 github.com/cloudflare/circl/ecc/goldilocks
 github.com/ProtonMail/go-crypto/openpgp/ed25519
 github.com/ProtonMail/go-crypto/openpgp/x25519
 github.com/ProtonMail/go-crypto/openpgp/x448
 github.com/go-git/go-billy/v5/osfs
 github.com/go-git/go-git/v5/plumbing
 github.com/go-git/gcfg/token
 github.com/go-git/gcfg/types
 gopkg.in/warnings.v0
 github.com/go-git/go-git/v5/internal/path_util
 github.com/go-git/go-git/v5/internal/revision
 github.com/go-git/go-git/v5/plumbing/cache
 github.com/cloudflare/circl/sign/ed448
 github.com/go-git/gcfg/scanner
 github.com/go-git/go-git/v5/plumbing/filemode
 github.com/go-git/go-git/v5/utils/binary
 github.com/go-git/go-git/v5/utils/sync
 github.com/go-git/go-git/v5/plumbing/format/index
 github.com/go-git/gcfg
 github.com/ProtonMail/go-crypto/openpgp/internal/ecc
 github.com/ProtonMail/go-crypto/openpgp/ed448
 github.com/go-git/go-git/v5/plumbing/format/idxfile
 github.com/go-git/go-git/v5/plumbing/storer
 github.com/emirpasic/gods/utils
github.com/go-git/go-git/v5/plumbing/format/diff
 github.com/emirpasic/gods/containers
 github.com/go-git/go-git/v5/plumbing/format/config
 github.com/sergi/go-diff/diffmatchpatch
 net/http/httptrace
 google.golang.org/grpc/internal/credentials
 github.com/emirpasic/gods/lists
 github.com/go-git/go-git/v5/plumbing/format/packfile
 github.com/emirpasic/gods/trees
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 golang.org/x/net/internal/httpcommon
 net/http
 github.com/ProtonMail/go-crypto/openpgp/ecdh
 google.golang.org/protobuf/internal/filetype
 github.com/ProtonMail/go-crypto/openpgp/ecdsa
 github.com/ProtonMail/go-crypto/openpgp/eddsa
 github.com/emirpasic/gods/lists/arraylist
 github.com/ProtonMail/go-crypto/openpgp/packet
 google.golang.org/protobuf/runtime/protoimpl
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 github.com/go-git/go-git/v5/storage
 google.golang.org/protobuf/types/descriptorpb
 google.golang.org/protobuf/types/known/anypb
 google.golang.org/protobuf/types/known/durationpb
 google.golang.org/protobuf/types/known/timestamppb
 github.com/emirpasic/gods/trees/binaryheap
 github.com/go-git/go-git/v5/utils/diff
 github.com/golang/protobuf/ptypes/duration
 github.com/golang/protobuf/ptypes/timestamp
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 github.com/golang/protobuf/ptypes/any
 google.golang.org/genproto/googleapis/rpc/status
 github.com/go-git/go-git/v5/utils/trace
 github.com/go-git/go-git/v5/utils/merkletrie
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/go-git/go-git/v5/storage/memory
 github.com/kevinburke/ssh_config
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 crypto/mlkem
 golang.org/x/crypto/chacha20
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 golang.org/x/crypto/curve25519
 golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 golang.org/x/net/internal/socks
 golang.org/x/crypto/ssh
 github.com/go-git/go-git/v5/plumbing/format/objfile
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 golang.org/x/net/proxy
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 github.com/go-git/go-git/v5/utils/merkletrie/index
 github.com/docker-library/bashbrew/pkg/tarscrub
github.com/docker-library/bashbrew/pkg/templatelib
 flag
 google.golang.org/protobuf/types/gofeaturespb
 github.com/russross/blackfriday/v2
 google.golang.org/protobuf/reflect/protodesc
 github.com/go-git/go-git/v5/storage/filesystem
 golang.org/x/term
 github.com/go-git/go-git/v5/plumbing/transport
 github.com/ProtonMail/go-crypto/openpgp
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 github.com/go-git/go-git/v5/plumbing/transport/git
 github.com/go-git/go-git/v5/plumbing/object
 github.com/golang/protobuf/proto
 github.com/cpuguy83/go-md2man/v2/md2man
 github.com/urfave/cli
 github.com/go-git/go-git/v5/plumbing/revlist
 github.com/go-git/go-git/v5/plumbing/transport/server
 golang.org/x/crypto/ssh/agent
 golang.org/x/crypto/ssh/knownhosts
 github.com/golang/protobuf/jsonpb
 github.com/golang/protobuf/ptypes
 google.golang.org/grpc/encoding/proto
 google.golang.org/grpc/credentials
 google.golang.org/grpc/binarylog/grpc_binarylog_v1
 github.com/go-git/go-git/v5/plumbing/transport/file
 github.com/skeema/knownhosts
 google.golang.org/grpc/credentials/insecure
 google.golang.org/grpc/internal/channelz
 google.golang.org/grpc/peer
 google.golang.org/grpc/internal/status
 google.golang.org/grpc/status
 github.com/xanzy/ssh-agent
 github.com/go-git/go-git/v5/plumbing/transport/ssh
 google.golang.org/grpc/internal/binarylog
 github.com/containerd/containerd/errdefs
 github.com/containerd/ttrpc
 github.com/containerd/containerd/labels
 github.com/containerd/containerd/filters
 github.com/containerd/containerd/platforms
 google.golang.org/grpc/channelz
 google.golang.org/grpc/internal/pretty
 github.com/containerd/containerd/identifiers
 google.golang.org/grpc/resolver
 github.com/containerd/containerd/content
 github.com/docker-library/bashbrew/architecture
 google.golang.org/grpc/internal
 google.golang.org/grpc/balancer/grpclb/state
 google.golang.org/grpc/internal/metadata
 google.golang.org/grpc/internal/resolver/passthrough
 google.golang.org/grpc/internal/transport/networktype
 google.golang.org/grpc/internal/resolver/dns
 google.golang.org/grpc/internal/resolver/unix
 google.golang.org/grpc/balancer
 github.com/containerd/containerd/images
 github.com/containerd/containerd/content/local
 google.golang.org/grpc/internal/serviceconfig
google.golang.org/grpc/balancer/base
 github.com/containerd/containerd/namespaces
 google.golang.org/grpc/internal/resolver
 google.golang.org/grpc/balancer/roundrobin
 google.golang.org/grpc/internal/balancer/gracefulswitch
 github.com/containerd/containerd/events/exchange
 github.com/containerd/containerd/diff
 github.com/containerd/containerd/images/archive
 github.com/containerd/containerd/oci
 github.com/containerd/containerd/remotes
 github.com/containerd/containerd/metadata
 github.com/containerd/containerd/plugin
 github.com/containerd/containerd/rootfs
 github.com/containerd/containerd/remotes/docker/schema1
 golang.org/x/net/http2
 net/http/httputil
 github.com/containerd/containerd/remotes/errors
 golang.org/x/net/context/ctxhttp
 github.com/docker-library/bashbrew/manifest
 golang.org/x/net/trace
 github.com/go-git/go-git/v5/plumbing/transport/http
 github.com/containerd/containerd/remotes/docker/auth
 github.com/containerd/containerd/remotes/docker
 github.com/go-git/go-git/v5/plumbing/transport/client
 github.com/go-git/go-git/v5
 github.com/docker-library/bashbrew/registry
 github.com/docker-library/bashbrew/pkg/gitfs
 google.golang.org/grpc/internal/transport
 google.golang.org/grpc
 github.com/containerd/containerd/api/services/containers/v1
 github.com/containerd/containerd/api/services/content/v1
 github.com/containerd/containerd/api/services/diff/v1
 github.com/containerd/containerd/api/services/events/v1
 github.com/containerd/containerd/api/services/images/v1
 github.com/containerd/containerd/api/services/introspection/v1
 github.com/containerd/containerd/api/services/leases/v1
 github.com/containerd/containerd/api/services/namespaces/v1
 github.com/containerd/containerd/api/services/snapshots/v1
 github.com/containerd/containerd/api/services/tasks/v1
 github.com/containerd/containerd/api/services/version/v1
 github.com/containerd/containerd/leases/proxy
 github.com/containerd/containerd/services/introspection
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-mips64le
 -rwxr-xr-x 1 root root 23M 14 de marzo 00:59 bin/bashbrew-mips64le*
 + archivo bin/bashbrew-mips64le
bin/bashbrew-mips64le: ejecutable ELF de 64 bits LSB, MIPS, MIPS-III versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=92b93d7dde800560eb3f6863e16e64a9b2d32cf5, sin símbolos de depuración
 + para bashbrewArch en $BASHBREW_ARCHES
 ++ bashbrew-arch-to-goenv.sh ppc64le
 + goEnv='export GOARCH=ppc64le GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 + eval 'export GOARCH=ppc64le GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 ++ export GOARCH=ppc64le GOOS=linux
 ++ GOARCH=ppc64le
 ++ GOOS=linux
 ++ unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64
 + '[' linux = windows ']'
 + ext=
 + LDFLAGS='-s -w'
 + case "$GOOS" in
 + LDFLAGS+=' -d'
 + targetBin=bin/bashbrew-ppc64le
 + go build -v -ldflags '-s -w -d' -tags netgo -installsuffix netgo -o bin/bashbrew-ppc64le ./cmd/bashbrew
 internal/byteorder
 internal/unsafeheader
 internal/coverage/rtcov
 internal/goos
 internal/godebugs
 internal/goarch
 internal/cpu
 internal/goexperiment
 internal/abi
 internal/profilerecord
 internal/runtime/atomic
 internal/msan
 internal/asan
 internal/runtime/math
 internal/runtime/sys
 internal/runtime/syscall
 sync/atomic
 math/bits
 internal/chacha8rand
 internal/bytealg
 unicode
 unicode/utf8
 internal/runtime/exithook
 internal/itoa
 crypto/internal/fips140/alias
 math
 crypto/internal/fips140deps/byteorder
 crypto/internal/fips140deps/cpu
 cmp
 crypto/internal/fips140/subtle
 crypto/internal/boring/sig
 encoding
 unicode/utf16
 internal/stringslite
 log/internal
 internal/nettrace
 container/list
 vendor/golang.org/x/crypto/cryptobyte/asn1
 vendor/golang.org/x/crypto/internal/alias
 google.golang.org/protobuf/internal/flags
 google.golang.org/protobuf/internal/set
 google.golang.org/grpc/attributes
 google.golang.org/grpc/serviceconfig
 github.com/klauspost/compress/internal/le
 github.com/containerd/containerd/defaults
 github.com/containerd/containerd/services
 image/color
 github.com/ProtonMail/go-crypto/internal/byteutil
 golang.org/x/crypto/cryptobyte/asn1
 github.com/pjbgf/sha1cd/internal
 github.com/pjbgf/sha1cd/ubc
 github.com/go-git/go-git/v5/plumbing/color
golang.org/x/crypto/internal/alias
 github.com/golang/groupcache/lru
 github.com/klauspost/compress
 internal/race
 internal/runtime/maps
 internal/sync
 runtime
 iter
 weak
 internal/reflectlite
 sync
 crypto/subtle
 github.com/containerd/containerd/version
 slices
 maps
 internal/bisect
 google.golang.org/grpc/internal/grpcsync
 internal/testlog
 unique
 internal/singleflight
 google.golang.org/protobuf/internal/pragma
 google.golang.org/grpc/internal/buffer
 errors
 sort
 internal/oserror
 path
 strconv
 math/rand/v2
 io
 syscall
 internal/godebug
 vendor/golang.org/x/net/dns/dnsmessage
 github.com/moby/locker
 golang.org/x/crypto/cast5
 bytes
 strings
 hash
 crypto/internal/randutil
 github.com/gogo/protobuf/sortkeys
 hash/crc32
 crypto
 crypto/internal/fips140deps/godebug
 reflect
 net/netip
 math/rand
 internal/saferio
 vendor/golang.org/x/text/transform
 hash/fnv
 bufio
 crypto/internal/fips140
 crypto/internal/impl
 html
 regexp/syntax
 crypto/internal/fips140/sha256
 crypto/internal/fips140/sha3
 crypto/internal/fips140/sha512
 crypto/tls/internal/fips140tls
 crypto/sha3
 net/http/internal/ascii
 golang.org/x/text/transform
 github.com/docker-library/bashbrew/pkg/stripper
 crypto/internal/fips140/hmac
 golang.org/x/crypto/openpgp/errors
 crypto/internal/fips140hash
 compress/bzip2
 crypto/internal/fips140/check
 hash/adler32
 golang.org/x/crypto/openpgp/s2k
 crypto/internal/fips140/aes
 crypto/internal/fips140/nistec/fiat
 crypto/internal/fips140/edwards25519/field
 crypto/internal/fips140/bigmod
 time
 internal/syscall/unix
 internal/syscall/execenv
 crypto/internal/fips140/edwards25519
 crypto/internal/fips140/hkdf
 regexp
 crypto/internal/fips140/tls12
 crypto/internal/fips140/tls13
 image
 pault.ag/go/topsort
 github.com/docker-library/bashbrew/pkg/dockerfile
 container/heap
 github.com/cloudflare/circl/sign
 github.com/cloudflare/circl/internal/sha3
 crypto/fips140
 golang.org/x/crypto/blowfish
image/internal/imageutil
 github.com/go-git/go-git/v5/internal/url
 image/jpeg
 context
 internal/poll
 io/fs
 google.golang.org/grpc/backoff
 google.golang.org/grpc/internal/grpcrand
 google.golang.org/grpc/keepalive
 google.golang.org/grpc/internal/backoff
 crypto/internal/fips140/nistec
 google.golang.org/grpc/tap
 github.com/containerd/containerd/gc
 golang.org/x/net/context
 golang.org/x/sync/semaphore
 internal/filepathlite
 embed
 github.com/jbenet/go-context/io
 github.com/go-git/go-git/v5/utils/ioutil
 google.golang.org/protobuf/internal/editiondefaults
 os
 encoding/binary
 internal/fmtsort
 vendor/golang.org/x/crypto/internal/poly1305
 github.com/klauspost/compress/zstd/internal/xxhash
 github.com/klauspost/compress/internal/snapref
 encoding/base64
 golang.org/x/crypto/blake2b
 golang.org/x/sys/unix
 golang.org/x/crypto/internal/poly1305
 crypto/internal/sysrand
 fmt
 path/filepath
 net
 crypto/internal/entropy
 encoding/pem
 io/ioutil
 crypto/internal/fips140/drbg
 google.golang.org/protobuf/internal/detrand
 google.golang.org/grpc/internal/envconfig
 crypto/internal/fips140/aes/gcm
 crypto/internal/fips140only
 crypto/internal/fips140/ecdh
 crypto/internal/fips140/ecdsa
 crypto/internal/fips140/ed25519
 crypto/internal/fips140/mlkem
 crypto/md5
 crypto/rc4
 crypto/internal/fips140/rsa
 crypto/cipher
 os/exec
 os/signal
 encoding/hex
 encoding/json
 crypto/internal/boring
 os/user
 log
 crypto/sha256
 crypto/sha512
 archive/tar
 compress/flate
 net/url
 text/template/parse
 golang.org/x/net/internal/timeseries
 math/big
 compress/gzip
 crypto/aes
 crypto/des
 crypto/ecdh
 crypto/hmac
 vendor/golang.org/x/crypto/chacha20
 text/template
 crypto/sha1
 vendor/golang.org/x/crypto/chacha20poly1305
 vendor/golang.org/x/text/unicode/bidi
 vendor/golang.org/x/text/unicode/norm
 vendor/golang.org/x/net/http2/hpack
 github.com/gogo/protobuf/proto
 net/textproto
 mime
 vendor/golang.org/x/text/secure/bidirule
 html/template
 mime/quotedprintable
net/http/internal
 text/tabwriter
 google.golang.org/grpc/internal/grpclog
 google.golang.org/protobuf/internal/errors
 google.golang.org/grpc/grpclog
 google.golang.org/protobuf/encoding/protowire
 go/token
 vendor/golang.org/x/net/idna
 crypto/rand
 crypto/elliptic
 crypto/internal/boring/bbig
 encoding/asn1
 crypto/ed25519
 crypto/internal/hpke
 crypto/rsa
 crypto/dsa
 vendor/golang.org/x/net/http/httpguts
 vendor/golang.org/x/net/http/httpproxy
 google.golang.org/grpc/connectivity
 google.golang.org/protobuf/reflect/protoreflect
 google.golang.org/protobuf/internal/version
 google.golang.org/grpc/metadata
 mime/multipart
 google.golang.org/grpc/codes
 golang.org/x/text/unicode/bidi
 golang.org/x/text/unicode/norm
 google.golang.org/grpc/internal/grpcutil
 google.golang.org/grpc/internal/balancerload
 golang.org/x/net/http2/hpack
 google.golang.org/grpc/encoding google.golang.org/grpc/internal/syscall
 google.golang.org/grpc/stats
 google.golang.org/protobuf/internal/encoding/messageset
 vendor /
 golang.org/x/crypto/cryptobyte
 crypto/x509/pkix
 google.golang.org/protobuf/internal/strs
 google.golang.org/protobuf/internal/genid
 google.golang.org/protobuf/internal/order
 google.golang.org/protobuf/reflect/protoregistry
 google.golang.org/protobuf/runtime/protoiface
 google.golang.org/protobuf/internal/encoding/text
 google.golang.org/protobuf/internal/descfmt
 google.golang.org/protobuf/internal/descopts
 google.golang.org/protobuf/internal/encoding/json
 golang.org/x/text/secure/bidirule
 google.golang.org/protobuf/proto
 github.com/opencontainers/go-digest
 crypto/ecdsa
 github.com/pkg/errors
 github.com/sirupsen/logrus
 google.golang.org/protobuf/internal/encoding/defval
 github.com/containerd/containerd/pkg/userns
 github.com/containerd/continuity/sysx
 golang.org/x/sync/errgroup
 github.com/klauspost/compress/fse
 runtime/debug
 golang.org/x/sys/execabs
 golang.org/x/net/idna
 github.com/containerd/fifo
 github.com/opencontainers/image-spec/specs-go
 github.com/opencontainers/image-spec/specs-go/v1
 github.com/klauspost/compress/huff0
 github.com/moby/sys/mountinfo
 google.golang.org/protobuf/encoding/prototext
 google.golang.org/protobuf/internal/filedesc
crypto/x509
 github.com/containerd/containerd/log
 github.com/containerd/continuity/fs
 github.com/containerd/containerd/cio
 github.com/containerd/containerd/mount
 golang.org/x/net/http/httpguts
 github.com/containerd/containerd/reference
 github.com/containerd/containerd/archive
 github.com/containerd/containerd/reference/docker
 github.com/klauspost/compress/zstd
 github.com/containerd/containerd/leases
 github.com/containerd/containerd/pkg/cap
 github.com/opencontainers/runc/libcontainer/user
 github.com/containerd/containerd/snapshots
 github.com/opencontainers/runtime-spec/specs-go
 github.com/containerd/containerd/pkg/dialer
 github.com/containerd/containerd/pkg/kmutex
 github.com/docker/go-events
 github.com/opencontainers/image-spec/identity
 database/sql/driver
 github.com/moby/sys/signal
 github.com/opencontainers/selinux/pkg/pwalkdir
 github.com/opencontainers/selinux/go-selinux
 go.etcd.io/bbolt
 golang.org/x/crypto/openpgp/armor
 compress/zlib
 github.com/google/uuid
 google.golang.org/protobuf/internal/encoding/tag
 google.golang.org/protobuf/encoding/protojson
 google.golang.org/protobuf/internal/impl
 golang.org/x/crypto/openpgp/elgamal
 golang.org/x/crypto/openpgp/packet
 crypto/tls
 github.com/opencontainers/selinux/go-selinux/label
 pault.ag/go/debian/version
 pault.ag/go/debian/hashio
 pault.ag/go/debian/dependency
 pault.ag/go/debian/internal
 github.com/docker-library/bashbrew/pkg/execpipe
 github.com/gogo/protobuf/types
 github.com/containerd/containerd/runtime/linux/runctypes
 github.com/containerd/containerd/runtime/v2/runc/options
 dario.cat/mergo
 github.com/ProtonMail/go-crypto/openpgp/errors
 github.com/containerd/containerd/archive/compression
 golang.org/x/crypto/openpgp
 golang.org/x/crypto/openpgp/clearsign
 github.com/ProtonMail/go-crypto/openpgp/armor
 github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
 github.com/ProtonMail/go-crypto/eax
 github.com/ProtonMail/go-crypto/ocb
 github.com/ProtonMail/go-crypto/bitcurves
 github.com/ProtonMail/go-crypto/brainpool
 github.com/ProtonMail/go-crypto/openpgp/internal/encoding
 pault.ag/go/debian/control
 github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
 golang.org/x/crypto/cryptobyte
 github.com/cloudflare/circl/math
github.com/ProtonMail/go-crypto/openpgp/elgamal
golang.org/x/crypto/argon2
golang.org/x/crypto/hkdf
golang.org/x/sys/cpu
github.com/go-git/go-billy/v5
golang.org/x/crypto/sha3
github.com/ProtonMail/go-crypto/openpgp/s2k
github.com/cyphar/filepath-securejoin
github.com/go-git/go-billy/v5/helper/polyfill
github.com/go-git/go-billy/v5/helper/chroot
github.com/cloudflare/circl/internal/conv
github.com/go-git/go-billy/v5/util
github.com/pjbgf/sha1cd
encoding/gob
github.com/cloudflare/circl/math/fp25519
github.com/cloudflare/circl/math/fp448
github.com/cloudflare/circl/math/mlsbset
github.com/cloudflare/circl/dh/x25519
github.com/cloudflare/circl/sign/ed25519
github.com/cloudflare/circl/dh/x448
github.com/cloudflare/circl/ecc/goldilocks
github.com/ProtonMail/go-crypto/openpgp/x25519
github.com/ProtonMail/go-crypto/openpgp/x448
github.com/go-git/go-billy/v5/osfs
github.com/ProtonMail/go-crypto/openpgp/ed25519
github.com/go-git/go-git/v5/plumbing/hash
github.com/go-git/gcfg/token
github.com/go-git/go-git/v5/plumbing
github.com/go-git/gcfg/scanner
github.com/go-git/gcfg/types
github.com/cloudflare/circl/sign/ed448
gopkg.in/warnings.v0
github.com/go-git/go-git/v5/internal/path_util
github.com/go-git/go-git/v5/internal/revision
github.com/go-git/go-git/v5/plumbing/filemode
github.com/go-git/go-git/v5/utils/sync
github.com/go-git/go-git/v5/plumbing/cache
github.com/go-git/go-git/v5/utils/binary
github.com/go-git/go-git/v5/plumbing/format/index
github.com/ProtonMail/go-crypto/openpgp/ed448
github.com/ProtonMail/go-crypto/openpgp/internal/ecc
github.com/go-git/go-git/v5/plumbing/format/idxfile
github.com/emirpasic/gods/utils
github.com/ProtonMail/go-crypto/openpgp/ecdh
github.com/ProtonMail/go-crypto/openpgp/ecdsa
github.com/ProtonMail/go-crypto/openpgp/eddsa
github.com/go-git/go-git/v5/plumbing/storer
github.com/emirpasic/gods/containers
github.com/ProtonMail/go-crypto/openpgp/packet
github.com/go-git/go-git/v5/plumbing/format/diff
github.com/emirpasic/gods/lists
github.com/go-git/go-git/v5/plumbing/format/packfile
github.com/emirpasic/gods/lists/arraylist
github.com/containerd/containerd/api/types
github.com/containerd/typeurl
github.com/gogo/googleapis/google/rpc
github.com/containerd/containerd/api/types/task
github.com/containerd/containerd/containers
 github.com/containerd/containerd/events
 github.com/containerd/containerd/metadata/boltutil
 github.com/go-git/gcfg
 github.com/emirpasic/gods/trees
 github.com/emirpasic/gods/trees/binaryheap
 github.com/sergi/go-diff/diffmatchpatch
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 net/http/httptrace
 google.golang.org/protobuf/internal/filetype
 google.golang.org/grpc/internal/credentials
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 github.com/go-git/go-git/v5/utils/merkletrie
 net/http
 golang.org/x/net/internal/httpcommon
 github.com/go-git/go-git/v5/plumbing/format/config
 github.com/go-git/go-git/v5/utils/trace
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 github.com/go-git/go-git/v5/utils/diff
 google.golang.org/protobuf/runtime/protoimpl
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 github.com/go-git/go-git/v5/plumbing/format/objfile
 google.golang.org/protobuf/types/descriptorpb
 google.golang.org/protobuf/types/known/anypb
 google.golang.org/protobuf/types/known/durationpb
 google.golang.org/protobuf/types/known/timestamppb
 github.com/ProtonMail/go-crypto/openpgp
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 github.com/golang/protobuf/ptypes/duration
 github.com/golang/protobuf/ptypes/any
 google.golang.org/genproto/googleapis/rpc/status
 github.com/golang/protobuf/ptypes/timestamp
 github.com/go-git/go-git/v5/storage
 github.com/kevinburke/ssh_config
 crypto/mlkem
 github.com/go-git/go-git/v5/storage/memory
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 golang.org/x/crypto/chacha20
 golang.org/x/crypto/curve25519
 golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 golang.org/x/net/internal/socks
 golang.org/x/net/proxy
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 golang.org/x/crypto/ssh
 github.com/go-git/go-git/v5/utils/merkletrie/index
 github.com/go-git/go-git/v5/plumbing/object
 github.com/docker-library/bashbrew/pkg/tarscrub
 github.com/docker-library/bashbrew/pkg/templatelib
 flag
 google.golang.org/protobuf/types/gofeaturespb
 github.com/go-git/go-git/v5/storage/filesystem
 github.com/russross/blackfriday/v2
google.golang.org/protobuf/reflect/protodesc
 golang.org/x/term
 github.com/go-git/go-git/v5/plumbing/transport
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 github.com/go-git/go-git/v5/plumbing/transport/git
 github.com/go-git/go-git/v5/plumbing/revlist
 github.com/golang/protobuf/proto
 github.com/cpuguy83/go-md2man/v2/md2man
 github.com/go-git/go-git/v5/plumbing/transport/server
 github.com/urfave/cli
 github.com/go-git/go-git/v5/plumbing/transport/file
 google.golang.org/grpc/credentials
 github.com/golang/protobuf/jsonpb
 google.golang.org/grpc/encoding/proto
 github.com/golang/protobuf/ptypes
 google.golang.org/grpc/binarylog/grpc_binarylog_v1
 google.golang.org/grpc/credentials/insecure
 google.golang.org/grpc/internal/channelz
 google.golang.org/grpc/peer
 google.golang.org/grpc/internal/status
 golang.org/x/crypto/ssh/knownhosts
 golang.org/x/crypto/ssh/agent
 google.golang.org/grpc/status
 github.com/skeema/knownhosts
 google.golang.org/grpc/internal/binarylog
 github.com/containerd/containerd/errdefs
 github.com/containerd/ttrpc
 google.golang.org/grpc/internal/pretty
 github.com/containerd/containerd/labels
 github.com/containerd/containerd/filters
 google.golang.org/grpc/channelz
 github.com/containerd/containerd/platforms
 github.com/containerd/containerd/identifiers
 google.golang.org/grpc/resolver
 github.com/xanzy/ssh-agent
 github.com/containerd/containerd/content
 google.golang.org/grpc/internal
 google.golang.org/grpc/internal/metadata
 google.golang.org/grpc/balancer/grpclb/state
 google.golang.org/grpc/internal/resolver/passthrough
 google.golang.org/grpc/internal/transport/networktype
 google.golang.org/grpc/internal/resolver/dns
 github.com/docker-library/bashbrew/architecture
 google.golang.org/grpc/balancer
 github.com/go-git/go-git/v5/plumbing/transport/ssh
 google.golang.org/grpc/internal/serviceconfig
 google.golang.org/grpc/balancer/base
 google.golang.org/grpc/internal/resolver/unix
 google.golang.org/grpc/internal/resolver
 github.com/containerd/containerd/images
 github.com/containerd/containerd/content/local
 github.com/containerd/containerd/namespaces
 google.golang.org/grpc/balancer/roundrobin
 google.golang.org/grpc/internal/balancer/gracefulswitch
 github.com/containerd/containerd/events/exchange
github.com/containerd/containerd/plugin
 github.com/containerd/containerd/diff
 github.com/containerd/containerd/images/archive
 github.com/containerd/containerd/oci
 github.com/containerd/containerd/remotes
 github.com/containerd/containerd/metadata
 github.com/containerd/containerd/rootfs
 github.com/containerd/containerd/remotes/docker/schema1
 github.com/containerd/containerd/remotes/errors
 net/http/httputil
 golang.org/x/net/http2
 golang.org/x/net/context/ctxhttp
 golang.org/x/net/trace
 github.com/docker-library/bashbrew/manifest
 github.com/go-git/go-git/v5/plumbing/transport/http
 github.com/containerd/containerd/remotes/docker/auth
 github.com/containerd/containerd/remotes/docker
 github.com/go-git/go-git/v5/plumbing/transport/client
 github.com/go-git/go-git/v5
 github.com/docker-library/bashbrew/registry
 github.com/docker-library/bashbrew/pkg/gitfs
 google.golang.org/grpc/internal/transport
 google.golang.org/grpc
 github.com/containerd/containerd/api/services/events/v1
 github.com/containerd/containerd/api/services/introspection/v1
 github.com/containerd/containerd/api/services/leases/v1
 github.com/containerd/containerd/api/services/images/v1
 github.com/containerd/containerd/api/services/namespaces/v1
 github.com/containerd/containerd/api/services/diff/v1
 github.com/containerd/containerd/api/services/containers/v1
 github.com/containerd/containerd/api/services/content/v1
 github.com/containerd/containerd/api/services/snapshots/v1
 github.com/containerd/containerd/api/services/tasks/v1
 github.com/containerd/containerd/api/services/version/v1
 github.com/containerd/containerd/services/introspection
 github.com/containerd/containerd/leases/proxy
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-ppc64le
 -rwxr-xr-x 1 root root 20M Mar 14 01:00 bin/bashbrew-ppc64le*
 + file bin/bashbrew-ppc64le
 bin/bashbrew-ppc64le: ELF 64-bit LSB ejecutable, PowerPC de 64 bits o Cisco 7500, ABI OpenPOWER ELF V2, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=6449f3c37f50c43272d3d6e2f3df3450706060e1, sin símbolos de depuración
 + para bashbrewArch en $BASHBREW_ARCHES
 ++ bashbrew-arch-to-goenv.sh riscv64
 + goEnv='export GOARCH=riscv64 GOOS=linux
unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 + eval 'export GOARCH=riscv64 GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 ++ export GOARCH=riscv64 GOOS=linux
 ++ GOARCH=riscv64
 ++ GOOS=linux
 ++ unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64
 + '[' linux = windows ']'
 + ext=
 + LDFLAGS='-s -w'
 + case "$GOOS" in
 + LDFLAGS+=' -d'
 + targetBin=bin/bashbrew-riscv64
 + go build -v -ldflags '-s -w -d' -tags netgo -installsuffix netgo -o bin/bashbrew-riscv64 ./cmd/bashbrew
 internal/godebugs
 internal/goarch internal
 /goexperiment
 internal/unsafeheader
 internal/goos
 internal/coverage/rtcov
 internal/cpu
 internal/byteorder
 internal/profilerecord
 internal/runtime/atomic
 internal/asan
 internal/msan
 internal/runtime/math
 internal/abi
 internal/runtime/sys
 internal/runtime/syscall
 math/bits
 sync/atomic
 internal/chacha8rand
 internal/bytealg
 unicode
 unicode/utf8
 internal/itoa
 crypto/internal/fips140/alias
 crypto/internal/fips140deps/byteorder
 math
 internal/runtime/exithook
 crypto/internal/fips140deps/cpu
 cmp
 crypto/internal/boring/sig
 encoding
 internal/stringslite
 unicode/utf16
 log/internal
 internal/nettrace
 container/list
 vendor/golang.org/x/crypto/cryptobyte/asn1
 vendor/golang.org/x/crypto/internal/alias
 google.golang.org/protobuf/internal/flags
 google.golang.org/protobuf/internal/set google.golang.org/grpc/attributes
 google.golang.org/grpc/serviceconfig
 github.com/klauspost/compress/internal/le
 github.com/containerd/containerd/defaults
 github.com/containerd/containerd/services
 image
 /color
 github.com/ProtonMail/go-crypto/internal/byteutil
 golang.org/x/crypto/cryptobyte/asn1
 github.com/pjbgf/sha1cd/internal
 github.com/pjbgf/sha1cd/ubc
 github.com/go-git/go-git/v5/plumbing/color
 github.com/golang/groupcache/lru
 golang.org/x/crypto/internal/alias
 github.com/klauspost/compress
 internal/race
 internal/runtime/maps
 internal/sync
 runtime
 iter
 internal/reflectlite
 crypto/internal/fips140/subtle
 sync
 weak
github.com/containerd/containerd/version
 slices
 maps
 crypto/subtle
 sort
 errors
 internal/oserror
 strconv
 path
 math/rand/v2
 vendor/golang.org/x/net/dns/dnsmessage
 golang.org/x/crypto/cast5
 pault.ag/go/topsort
 io
 internal/bisect
 syscall
 internal/testlog
 unique
 internal/singleflight
 internal/godebug
 bytes
 strings
 hash
 crypto/internal/randutil
 github.com/gogo/protobuf/sortkeys
 crypto
 reflect
 hash/crc32
 net/netip
 internal/saferio
 vendor/golang.org/x/text/transform
 crypto/internal/fips140deps/godebug
 math/rand
 hash/fnv
 google.golang.org/protobuf/internal/pragma
 google.golang.org/grpc/internal/buffer
 bufio
 crypto/internal/fips140
 html
 regexp/syntax
 crypto/internal/impl
 crypto/internal/fips140/sha256
 crypto/internal/fips140/sha3
 crypto/internal/fips140/sha512
 crypto/tls/internal/fips140tls
 net/http/internal/ascii
 google.golang.org/grpc/internal/grpcsync
 golang.org/x/text/transform
 github.com/moby/locker
 crypto/sha3
 crypto/internal/fips140/hmac
 github.com/docker-library/bashbrew/pkg/stripper
 crypto/internal/fips140/check
 golang.org/x/crypto/openpgp/errors
 compress/bzip2
 crypto/internal/fips140/aes
 crypto/internal/fips140/nistec/fiat
 crypto/internal/fips140/edwards25519/field
 crypto/internal/fips140/bigmod
 time
 internal/syscall/unix
 internal/syscall/execenv
 crypto/internal/fips140hash
 crypto/internal/fips140/edwards25519
 crypto/internal/fips140/hkdf
 crypto/internal/fips140/tls12
 regexp
 crypto/internal/fips140/tls13
 hash/adler32
 golang.org/x/crypto/openpgp/s2k
 image
 github.com/docker-library/bashbrew/pkg/dockerfile
 container/heap
 github.com/cloudflare/circl/sign
 crypto/fips140
 golang.org/x/crypto/blowfish
 image/internal/imageutil
 github.com/go-git/go-git/v5/internal/url
 imagen/jpeg
 io/fs
 google.golang.org/grpc/backoff
 google.golang.org/grpc/internal/grpcrand
 contexto
 internal/poll
 google.golang.org/grpc/keepalive
 internal/fmtsort
 encoding/binary
google.golang.org/grpc/internal/backoff
crypto/internal/fips140/nistec
embed
internal/filepathlite
google.golang.org/grpc/tap
golang.org/x/sync/semaphore
github.com/containerd/containerd/gc
golang.org/x/net/context
github.com/jbenet/go-context/io
google.golang.org/protobuf/internal/editiondefaults
github.com/go-git/go-git/v5/utils/ioutil
os
vendor/golang.org/x/crypto/internal/poly1305
github.com/klauspost/compress/zstd/internal/xxhash
github.com/klauspost/compress/internal/snapref
encoding/base64
github.com/cloudflare/circl/internal/sha3
golang.org/x/sys/unix
golang.org/x/crypto/blake2b
golang.org/x/crypto/internal/poly1305
encoding/pem
golang.org/x/crypto/openpgp/armor
golang.org/x/crypto/argon2
fmt
crypto/internal/sysrand
path/filepath
io/ioutil
google.golang.org/protobuf/internal/detrand
google.golang.org/grpc/internal/envconfig
net
os/signal
crypto/internal/entropy
crypto/internal/fips140/drbg
pault.ag/go/debian/internal
crypto/internal/fips140/aes/gcm
crypto/internal/fips140only
crypto/internal/fips140/ecdh
crypto/internal/fips140/ecdsa
crypto/internal/fips140/ed25519
crypto/internal/fips140/mlkem
crypto/md5
crypto/cipher
crypto/rc4
crypto/internal/fips140/rsa
crypto/internal/boring
crypto/des
crypto/sha256
crypto/sha512
crypto/aes
crypto/ecdh
crypto/hmac
vendor/golang.org/x/crypto/chacha20
crypto/sha1
os/exec
github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
github.com/ProtonMail/go-crypto/eax
golang.org/x/crypto/hkdf
golang.org/x/sys/cpu
github.com/go-git/go-billy/v5
vendor/golang.org/x/crypto/chacha20poly1305
crypto/mlkem
github.com/go-git/go-billy/v5/helper/polyfill
golang.org/x/crypto/sha3
encoding/hex
encoding/json
os/user
log
compress/flate
net/url
archive/tar
text/template/parse
golang.org/x/net/internal/timeseries
math/big
vendor/golang.org/x/text/unicode/bidi
compress/gzip
vendor/golang.org/x/text/unicode/norm
vendor/golang.org/x/net/http2/hpack
mime
mime/quotedprintable
text/template
vendor/golang.org/x/text/secure/bidirule
net/http/internal
text/tabwriter
google.golang.org/grpc/internal/grpclog
google.golang.org/protobuf/internal/errors
go/token
google.golang.org/protobuf/encoding/protowire
net/textproto
github.com/gogo/protobuf/proto
google.golang.org/grpc/grpclog
google.golang.org/protobuf/reflect/protoreflect
vendor/golang.org/x/net/idna
google.golang.org/protobuf/internal/version
google.golang.org/grpc/metadata
google.golang.org/grpc/connectivity
google.golang.org/grpc/codes
google.golang.org/grpc/internal/grpcutil
google.golang.org/grpc/internal/balancerload
golang.org/x/text/unicode/bidi
google.golang.org/grpc/encoding
golang.org/x/text/unicode/norm
golang.org/x/net/http2/hpack
crypto/rand
crypto/elliptic
crypto/internal/boring/bbig
html/template
encoding/asn1
crypto/ed25519
crypto/internal/hpke
crypto/rsa
crypto/dsa
vendor/golang.org/x/net/http/httpguts
vendor/golang.org/x/net/http/httpproxy
mime/multipart
google.golang.org/protobuf/internal/encoding/messageset
google.golang.org/protobuf/internal/strs
google.golang.org/protobuf/internal/encoding/text
google.golang.org/protobuf/internal/genid
google.golang.org/protobuf/internal/order
google.golang.org/protobuf/reflect/protoregistry
google.golang.org/protobuf/runtime/protoiface
google.golang.org/protobuf/internal/descfmt
google.golang.org/protobuf/internal/descopts
google.golang.org/protobuf/internal/encoding/json
vendor/golang.org/x/crypto/cryptobyte
crypto/x509/pkix
google.golang.org/protobuf/internal/encoding/defval
google.golang.org/protobuf/proto
golang.org/x/text/secure/bidirule
google.golang.org/grpc/internal/syscall
google.golang.org/grpc/stats
crypto/ecdsa
golang.org/x/net/idna
github.com/opencontainers/go-digest
github.com/pkg/errors
github.com/sirupsen/logrus
github.com/containerd/containerd/pkg/userns
github.com/containerd/continuity/sysx
golang.org/x/sync/errgroup
github.com/klauspost/compress/fse
runtime/debug
golang.org/x/sys/execabs
github.com/containerd/fifo
github.com/opencontainers/image-spec/specs-go
google.golang.org/protobuf/encoding/prototext
google.golang.org/protobuf/internal/filedesc
github.com/containerd/containerd/cio
 github.com/klauspost/compress/huff0
 golang.org/x/net/http/httpguts
 crypto/x509
 github.com/opencontainers/image-spec/specs-go/v1
 github.com/containerd/containerd/log
 github.com/containerd/continuity/fs
 github.com/moby/sys/mountinfo
 github.com/containerd/containerd/reference
 github.com/containerd/containerd/reference/docker
 github.com/containerd/containerd/mount
 github.com/containerd/containerd/leases
 github.com/containerd/containerd/pkg/cap
 github.com/containerd/containerd/archive
 github.com/opencontainers/runc/libcontainer/user
 github.com/containerd/containerd/snapshots
 github.com/klauspost/compress/zstd
 github.com/opencontainers/runtime-spec/specs-go
 github.com/containerd/containerd/pkg/dialer
 github.com/containerd/containerd/pkg/kmutex
 github.com/docker/go-events
 google.golang.org/protobuf/internal/encoding/tag
 google.golang.org/protobuf/encoding/protojson
 github.com/opencontainers/image-spec/identity
 database/sql/driver
 github.com/moby/sys/signal
 google.golang.org/protobuf/internal/impl
 github.com/google/uuid
 github.com/opencontainers/selinux/pkg/pwalkdir
 github.com/opencontainers/selinux/go-selinux
 go.etcd.io/bbolt
 compress/zlib
 golang.org/x/crypto/openpgp/elgamal
 pault.ag/go/debian/version
 github.com/opencontainers/selinux/go-selinux/label
 golang.org/x/crypto/openpgp/packet
 pault.ag/go/debian/dependency
 pault.ag/go/debian/hashio
 github.com/docker-library/bashbrew/pkg/execpipe
 crypto/tls
 dario.cat/mergo
 github.com/ProtonMail/go-crypto/openpgp/errors
 github.com/ProtonMail/go-crypto/openpgp/armor
 golang.org/x/crypto/openpgp
 golang.org/x/crypto/openpgp/clearsign
 github.com/ProtonMail/go-crypto/ocb
 github.com/gogo/protobuf/types
 github.com/containerd/containerd/runtime/linux/runctypes
 github.com/containerd/containerd/runtime/v2/runc/options
 github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
 github.com/ProtonMail/go-crypto/bitcurves
 pault.ag/go/debian/control
 github.com/ProtonMail/go-crypto/brainpool
 github.com/ProtonMail/go-crypto/openpgp/internal/encoding
 golang.org/x/crypto/cryptobyte
 github.com/cloudflare/circl/math
 github.com/ProtonMail/go-crypto/openpgp/elgamal
 github.com/ProtonMail/go-crypto/openpgp/s2k
 github.com/cyphar/filepath-securejoin
github.com/go-git/go-billy/v5/helper/chroot
 github.com/containerd/containerd/archive/compression
 github.com/go-git/go-billy/v5/util
 github.com/pjbgf/sha1cd
 github.com/cloudflare/circl/internal/conv
 encoding/gob
 github.com/go-git/go-git/v5/plumbing/hash
 github.com/go-git/go-git/v5/plumbing
 github.com/go-git/gcfg/token
 github.com/cloudflare/circl/math/fp25519
 github.com/cloudflare/circl/math/fp448
 github.com/cloudflare/circl/dh/x25519
 github.com/cloudflare/circl/sign/ed25519
 github.com/cloudflare/circl/math/mlsbset
 github.com/cloudflare/circl/dh/x448
 github.com/cloudflare/circl/ecc/goldilocks
 github.com/ProtonMail/go-crypto/openpgp/x25519
 github.com/go-git/go-billy/v5/osfs
 github.com/ProtonMail/go-crypto/openpgp/x448
 github.com/cloudflare/circl/sign/ed448
 github.com/go-git/gcfg/scanner
 github.com/ProtonMail/go-crypto/openpgp/ed25519
 github.com/go-git/gcfg/types
 gopkg.in/warnings.v0
 github.com/ProtonMail/go-crypto/openpgp/internal/ecc
 github.com/ProtonMail/go-crypto/openpgp/ed448
 github.com/go-git/go-git/v5/internal/path_util
 github.com/go-git/go-git/v5/internal/revision
 github.com/go-git/go-git/v5/plumbing/cache
 github.com/go-git/go-git/v5/plumbing/filemode
 github.com/go-git/go-git/v5/utils/binary
 github.com/go-git/go-git/v5/utils/sync
 github.com/go-git/go-git/v5/plumbing/format/index
 github.com/go-git/go-git/v5/plumbing/format/idxfile
 github.com/emirpasic/gods/utils
 github.com/ProtonMail/go-crypto/openpgp/ecdh
 github.com/ProtonMail/go-crypto/openpgp/ecdsa
 github.com/ProtonMail/go-crypto/openpgp/eddsa
 github.com/emirpasic/gods/containers
 github.com/ProtonMail/go-crypto/openpgp/packet
 github.com/go-git/go-git/v5/plumbing/storer
 github.com/go-git/go-git/v5/plumbing/format/diff
 github.com/emirpasic/gods/lists
 github.com/emirpasic/gods/lists/arraylist
 github.com/go-git/go-git/v5/plumbing/format/packfile
 google.golang.org/protobuf/internal/filetype
 github.com/containerd/containerd/api/types
 github.com/containerd/typeurl
 github.com/gogo/googleapis/google/rpc
 google.golang.org/protobuf/runtime/protoimpl
 github.com/containerd/containerd/api/types/task
 google.golang.org/protobuf/types/descriptorpb
 google.golang.org/protobuf/types/known/anypb
 net/http/httptrace
 google.golang.org/grpc/internal/credentials
google.golang.org/protobuf/types/known/durationpb
 github.com/golang/protobuf/ptypes/any
 github.com/golang/protobuf/ptypes/duration
 net/http
 google.golang.org/protobuf/types/known/timestamppb
 google.golang.org/genproto/googleapis/rpc/status
 github.com/golang/protobuf/ptypes/timestamp
 golang.org/x/net/internal/httpcommon
 github.com/containerd/containerd/containers
 github.com/containerd/containerd/events
 github.com/containerd/containerd/metadata/boltutil
 github.com/go-git/gcfg
 github.com/emirpasic/gods/trees
 github.com/emirpasic/gods/trees/binaryheap
 github.com/go-git/go-git/v5/plumbing/format/config
 github.com/sergi/go-diff/diffmatchpatch
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 github.com/go-git/go-git/v5/utils/trace
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 google.golang.org/protobuf/types/gofeaturespb
 github.com/go-git/go-git/v5/storage
 github.com/go-git/go-git/v5/utils/merkletrie
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/go-git/go-git/v5/utils/diff
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 github.com/go-git/go-git/v5/storage/memory
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 github.com/go-git/go-git/v5/plumbing/format/objfile
 google.golang.org/protobuf/reflect/protodesc
 github.com/kevinburke/ssh_config
 golang.org/x/crypto/chacha20
 golang.org/x/crypto/curve25519
 golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 golang.org/x/net/internal/socks
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 github.com/ProtonMail/go-crypto/openpgp
 golang.org/x/crypto/ssh
 golang.org/x/net/proxy
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 github.com/go-git/go-git/v5/utils/merkletrie/index
 github.com/golang/protobuf/proto
 github.com/docker-library/bashbrew/pkg/tarscrub
 github.com/docker-library/bashbrew/pkg/templatelib
 flag
 github.com/russross/blackfriday/v2
 github.com/go-git/go-git/v5/storage/filesystem
 github.com/go-git/go-git/v5/plumbing/transport
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 golang.org/x/term
 github.com/go-git/go-git/v5/plumbing/object
 github.com/go-git/go-git/v5/plumbing/transport/git
google.golang.org/grpc/encoding/proto
github.com/golang/protobuf/jsonpb
google.golang.org/grpc/credentials
github.com/golang/protobuf/ptypes
google.golang.org/grpc/binarylog/grpc_binarylog_v1
google.golang.org/grpc/internal/channelz
google.golang.org/grpc/credentials/insecure
google.golang.org/grpc/internal/status
google.golang.org/grpc/peer
github.com/cpuguy83/go-md2man/v2/md2man
google.golang.org/grpc/status
google.golang.org/grpc/internal/pretty
google.golang.org/grpc/resolver
github.com/urfave/cli
github.com/containerd/containerd/errdefs
google.golang.org/grpc/internal/binarylog
google.golang.org/grpc/channelz
github.com/containerd/ttrpc
google.golang.org/grpc/internal
google.golang.org/grpc/balancer
google.golang.org/grpc/internal/metadata
google.golang.org/grpc/balancer/base
google.golang.org/grpc/internal/serviceconfig
google.golang.org/grpc/balancer/roundrobin
google.golang.org/grpc/internal/balancer/gracefulswitch
google.golang.org/grpc/internal/resolver
google.golang.org/grpc/balancer/grpclb/state
google.golang.org/grpc/internal/resolver/passthrough
google.golang.org/grpc/internal/resolver/dns
google.golang.org/grpc/internal/transport/networktype
github.com/containerd/containerd/filters
google.golang.org/grpc/internal/resolver/unix
github.com/containerd/containerd/labels
github.com/containerd/containerd/platforms
github.com/containerd/containerd/identifiers
github.com/go-git/go-git/v5/plumbing/revlist
github.com/containerd/containerd/content
github.com/go-git/go-git/v5/plumbing/transport/server
github.com/go-git/go-git/v5/plumbing/transport/file
github.com/containerd/containerd/content/local
github.com/docker-library/bashbrew/architecture
github.com/containerd/containerd/images
github.com/containerd/containerd/namespaces
github.com/containerd/containerd/events/exchange
github.com/containerd/containerd/images/archive
github.com/containerd/containerd/oci
github.com/containerd/containerd/remotes
github.com/containerd/containerd/diff
github.com/containerd/containerd/plugin
github.com/containerd/containerd/metadata
github.com/containerd/containerd/remotes/docker/schema1
golang.org/x/crypto/ssh/knownhosts
golang.org/x/crypto/ssh/agent
github.com/containerd/containerd/rootfs
github.com/skeema/knownhosts
github.com/xanzy/ssh-agent
 github.com/go-git/go-git/v5/plumbing/transport/ssh
 net/http/httputil
 golang.org/x/net/http2
 github.com/containerd/containerd/remotes/errors
 golang.org/x/net/context/ctxhttp
 github.com/docker-library/bashbrew/manifest
 github.com/go-git/go-git/v5/plumbing/transport/http
 golang.org/x/net/trace
 github.com/containerd/containerd/remotes/docker/auth
 github.com/go-git/go-git/v5/plumbing/transport/client
 github.com/go-git/go-git/v5
 github.com/containerd/containerd/remotes/docker
 github.com/docker-library/bashbrew/registry
 github.com/docker-library/bashbrew/pkg/gitfs
 google.golang.org/grpc/internal/transport
 google.golang.org/grpc
 github.com/containerd/containerd/api/services/containers/v1
 github.com/containerd/containerd/api/services/content/v1
 github.com/containerd/containerd/api/services/diff/v1
 github.com/containerd/containerd/api/services/images/v1
 github.com/containerd/containerd/api/services/events/v1
 github.com/containerd/containerd/api/services/namespaces/v1
 github.com/containerd/containerd/api/services/introspection/v1
 github.com/containerd/containerd/api/services/leases/v1
 github.com/containerd/containerd/api/services/snapshots/v1
 github.com/containerd/containerd/api/services/tasks/v1
 github.com/containerd/containerd/api/services/version/v1
 github.com/containerd/containerd/services/introspection
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/leases/proxy
 github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-riscv64
 -rwxr-xr-x 1 root root 20M Mar 14 01:01 bin/bashbrew-riscv64*
 + archivo bin/bashbrew-riscv64
 bin/bashbrew-riscv64: ejecutable ELF de 64 bits LSB, UCB RISC-V, ABI de doble punto flotante, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=c4adfb02272eddffb4e2d49936853dd81af8e9e0, sin símbolos de depuración
 + para bashbrewArch en $BASHBREW_ARCHES
 ++ bashbrew-arch-to-goenv.sh s390x
 + goEnv='export GOARCH=s390x GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 + eval 'export GOARCH=s390x GOOS=linux
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64'
 ++ export GOARCH=s390x GOOS=linux
 ++ GOARCH=s390x
 ++ GOOS=linux
 ++ unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOAMD64 GOPPC64
 + '[' linux = windows ']'
+ ext=
+ LDFLAGS='-s -w'
+ case "$GOOS" in
+ LDFLAGS+=' -d'
+ targetBin=bin/bashbrew-s390x
+ go build -v -ldflags '-s -w -d' -tags netgo -installsuffix netgo -o bin/bashbrew-s390x ./cmd/bashbrew
internal/goos
internal/unsafeheader
internal/goexperiment
internal/godebugs
internal/goarch
internal/byteorder
internal/coverage/rtcov
internal/profilerecord
internal/cpu
internal/asan
internal/runtime/atomic
internal/runtime/syscall
sync/atomic
internal/abi
internal/msan
internal/runtime/math
internal/chacha8rand
internal/runtime/sys
math/bits
unicode
unicode/utf8
internal/runtime/exithook
internal/itoa
internal/bytealg
crypto/internal/fips140/alias
crypto/internal/fips140deps/byteorder
crypto/internal/fips140deps/cpu
math
cmp
crypto/internal/boring/sig
encoding
unicode/utf16
log/internal
internal/nettrace
container/list
vendor/golang.org/x/crypto/cryptobyte/asn1
internal/stringslite
vendor/golang.org/x/crypto/internal/alias
google.golang.org/protobuf/internal/flags
google.golang.org/protobuf/internal/set
google.golang.org/grpc/attributes
google.golang.org/grpc/serviceconfig
github.com/containerd/containerd/defaults
github.com/containerd/containerd/services
image/color
github.com/ProtonMail/go-crypto/internal/byteutil
golang.org/x/crypto/cryptobyte/asn1
github.com/pjbgf/sha1cd/internal
github.com/pjbgf/sha1cd/ubc
github.com/go-git/go-git/v5/plumbing/color
github.com/golang/groupcache/lru
golang.org/x/crypto/internal/alias
internal/race
internal/runtime/maps
internal/sync
github.com/klauspost/compress
runtime
iter
sync
crypto/internal/fips140/subtle
internal/reflectlite
weak
github.com/containerd/containerd/version
slices
maps
crypto/subtle
errors
sort
internal/bisect
internal/testlog
google.golang.org/grpc/internal/buffer
unique
internal/singleflight
google.golang.org/protobuf/internal/pragma
google.golang.org/grpc/internal/grpcsync
internal/oserror
strconv
path
math/rand/v2
 io
 internal/godebug
 syscall
 vendor/golang.org/x/net/dns/dnsmessage
 github.com/moby/locker
 golang.org/x/crypto/cast5
 github.com/gogo/protobuf/sortkeys
 pault.ag/go/topsort
 container/heap
 bytes
 strings
 hash
 crypto/internal/randutil
 hash/crc32
 internal/saferio
 hash/fnv
 crypto/internal/fips140deps/godebug
 math/rand
 hash/adler32
 vendor/golang.org/x/text/transform
 crypto
 reflect
 net/netip
 golang.org/x/text/transform
 golang.org/x/crypto/openpgp/errors
 github.com/cloudflare/circl/sign
 golang.org/x/crypto/blowfish
 golang.org/x/crypto/openpgp/s2k
 crypto/internal/impl
 bufio
 crypto/internal/fips140
 html
 regexp/syntax
 net/http/internal/ascii
 crypto/internal/fips140/sha256
 crypto/internal/fips140/sha3
 crypto/internal/fips140/sha512
 time
 internal/syscall/unix
 internal/syscall/execenv
 crypto/sha3
 crypto/tls/internal/fips140tls
 crypto/internal/fips140/hmac
 github.com/docker-library/bashbrew/pkg/stripper
 compress/bzip2
 crypto/internal/fips140hash
 image
 github.com/docker-library/bashbrew/pkg/dockerfile
 crypto/internal/fips140/check
 regexp
 crypto/internal/fips140/aes
 crypto/internal/fips140/nistec/fiat
 crypto/internal/fips140/edwards25519/field
 crypto/internal/fips140/bigmod
 crypto/internal/fips140/edwards25519
 crypto/internal/fips140/hkdf
 crypto/internal/fips140/tls12
 image/internal/imageutil
 github.com/go-git/go-git/v5/internal/url
 crypto/internal/fips140/tls13
 crypto/fips140
 image/jpeg
 context
 internal/poll
 io/fs
 google.golang.org/grpc/backoff
 google.golang.org/grpc/internal/grpcrand
 google.golang.org/grpc/keepalive
 google.golang.org/grpc/internal/backoff
 golang.org/x/sync/semaphore
 github.com/containerd/containerd/gc
 google.golang.org/grpc/tap
 golang.org/x/net/context
 internal/filepathlite
 embed
 github.com/jbenet/go-context/io
 crypto/internal/fips140/nistec
 github.com/go-git/go-git/v5/utils/ioutil
 google.golang.org/protobuf/internal/editiondefaults
 os
 encoding/binary
 internal/fmtsort
encoding/base64
github.com/klauspost/compress/internal/le
github.com/klauspost/compress/internal/snapref
github.com/klauspost/compress/zstd/internal/xxhash
github.com/cloudflare/circl/internal/sha3
golang.org/x/sys/unix
golang.org/x/crypto/blake2b
golang.org/x/crypto/openpgp/armor
encoding/pem
golang.org/x/crypto/argon2
crypto/internal/sysrand
path/filepath
fmt
vendor/golang.org/x/sys/cpu
net
io/ioutil
crypto/internal/entropy
crypto/internal/fips140/drbg
google.golang.org/protobuf/internal/detrand
google.golang.org/grpc/internal/envconfig
os/exec
os/signal
pault.ag/go/debian/internal
vendor/golang.org/x/crypto/internal/poly1305
crypto/internal/fips140/aes/gcm
crypto/internal/fips140only
crypto/internal/fips140/ecdh
crypto/internal/fips140/ecdsa
crypto/internal/fips140/ed25519
crypto/internal/fips140/mlkem
crypto/md5
crypto/cipher
crypto/rc4
encoding/hex
encoding/json
os/user
log
crypto/internal/boring
compress/flate
net/url
crypto/sha256
crypto/sha512
archive/tar
text/template/parse
golang.org/x/net/internal/timeseries
math/big
compress/gzip
crypto/aes
crypto/des
crypto/ecdh
crypto/hmac
vendor/golang.org/x/crypto/chacha20
text/template
crypto/internal/fips140/rsa
github.com/gogo/protobuf/proto
vendor/golang.org/x/crypto/chacha20poly1305
crypto/sha1
vendor/golang.org/x/text/unicode/bidi
vendor/golang.org/x/text/unicode/norm
vendor/golang.org/x/net/http2/hpack
mime
mime/quotedprintable
vendor/golang.org/x/text/secure/bidirule
net/http/internal
text/tabwriter
google.golang.org/grpc/internal/grpclog
html/template
google.golang.org/grpc/grpclog
google.golang.org/protobuf/internal/errors
go/token
crypto/rand
crypto/elliptic
crypto/internal/boring/bbig
encoding/asn1
crypto/ed25519
crypto/internal/hpke
crypto/rsa
crypto/dsa
google.golang.org/grpc/connectivity
vendor/golang.org/x/net/idna
google.golang.org/protobuf/encoding/protowire
net/textproto
google.golang.org/protobuf/internal/version
google.golang.org/grpc/metadata
 google.golang.org/protobuf/reflect/protoreflect
 crypto/x509/pkix
 vendor/golang.org/x/crypto/cryptobyte
 google.golang.org/grpc/codes
 google.golang.org/grpc/internal/grpcutil
 google.golang.org/grpc/internal/balancerload
 golang.org/x/text/unicode/bidi
 mime/multipart
 golang.org/x/text/unicode/norm
 google.golang.org/grpc/encoding
 golang.org/x/net/http2/hpack
 crypto/ecdsa
 vendor/golang.org/x/net/http/httpguts
 vendor/golang.org/x/net/http/httpproxy
 google.golang.org/grpc/internal/syscall
 google.golang.org/protobuf/internal/encoding/messageset
 google.golang.org/protobuf/internal/strs
 google.golang.org/protobuf/internal/order
 google.golang.org/protobuf/internal/genid
 google.golang.org/protobuf/reflect/protoregistry
 google.golang.org/protobuf/internal/encoding/text
 google.golang.org/protobuf/runtime/protoiface
 google.golang.org/protobuf/internal/descfmt
 google.golang.org/protobuf/internal/descopts
 google.golang.org/protobuf/internal/encoding/json
 golang.org/x/text/secure/bidirule
 google.golang.org/grpc/stats
 google.golang.org/protobuf/proto
 github.com/opencontainers/go-digest
 github.com/pkg/errors
 github.com/sirupsen/logrus
 github.com/containerd/containerd/pkg/userns
 github.com/containerd/continuity/sysx
 golang.org/x/sync/errgroup
 google.golang.org/protobuf/internal/encoding/defval
 golang.org/x/net/idna
 crypto/x509
 github.com/klauspost/compress/fse
 runtime/debug
 golang.org/x/sys/execabs
 github.com/klauspost/compress/huff0
 github.com/containerd/fifo
 github.com/opencontainers/image-spec/specs-go
 github.com/opencontainers/image-spec/specs-go/v1
 google.golang.org/protobuf/encoding/prototext
 google.golang.org/protobuf/internal/filedesc
 github.com/containerd/containerd/log
 golang.org/x/net/http/httpguts
 github.com/containerd/continuity/fs
 github.com/containerd/containerd/cio
 github.com/moby/sys/mountinfo
 github.com/containerd/containerd/reference
 github.com/containerd/containerd/reference/docker
 github.com/klauspost/compress/zstd
 github.com/containerd/containerd/mount
 github.com/containerd/containerd/leases
 github.com/containerd/containerd/archive
 github.com/containerd/containerd/pkg/cap
 github.com/opencontainers/runc/libcontainer/user
github.com/opencontainers/runtime-spec/specs-go
 github.com/containerd/containerd/pkg/dialer
 github.com/gogo/protobuf/types
 github.com/containerd/containerd/pkg/kmutex
 crypto/tls
 github.com/docker/go-events
 github.com/opencontainers/image-spec/identity
 github.com/containerd/containerd/snapshots
 github.com/containerd/containerd/runtime/linux/runctypes
 github.com/containerd/containerd/runtime/v2/runc/options
 database/sql/driver
 google.golang.org/protobuf/internal/encoding/tag
 google.golang.org/protobuf/encoding/protojson
 google.golang.org/protobuf/internal/impl
 github.com/google/uuid
 github.com/moby/sys/signal
 github.com/opencontainers/selinux/pkg/pwalkdir
 github.com/opencontainers/selinux/go-selinux
 go.etcd.io/bbolt
 compress/zlib
 golang.org/x/crypto/openpgp/elgamal
 pault.ag/go/debian/version
 github.com/opencontainers/selinux/go-selinux/label
 golang.org/x/crypto/openpgp/packet
 pault.ag/go/debian/dependency
 pault.ag/go/debian/hashio
 github.com/docker-library/bashbrew/pkg/execpipe
 dario.cat/mergo
 github.com/ProtonMail/go-crypto/openpgp/errors
 github.com/ProtonMail/go-crypto/openpgp/armor
 github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
 github.com/containerd/containerd/archive/compression
 github.com/ProtonMail/go-crypto/eax
 github.com/ProtonMail/go-crypto/ocb
 github.com/ProtonMail/go-crypto/bitcurves
 github.com/ProtonMail/go-crypto/brainpool
 github.com/ProtonMail/go-crypto/openpgp/internal/encoding
 golang.org/x/crypto/cryptobyte
 github.com/cloudflare/circl/math
 github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
 github.com/ProtonMail/go-crypto/openpgp/elgamal
 golang.org/x/crypto/hkdf
 github.com/ProtonMail/go-crypto/openpgp/s2k
 golang.org/x/crypto/openpgp
 golang.org/x/crypto/openpgp/clearsign
 golang.org/x/sys/cpu
 github.com/go-git/go-billy/v5
 github.com/cyphar/filepath-securejoin
 github.com/go-git/go-billy/v5/helper/polyfill
 github.com/go-git/go-billy/v5/helper/chroot
 github.com/containerd/containerd/api/types
 github.com/containerd/typeurl
 github.com/gogo/googleapis/google/rpc
 github.com/containerd/containerd/api/types/task
 github.com/containerd/containerd/containers
 github.com/containerd/containerd/metadata/boltutil
 github.com/containerd/containerd/events
 pault.ag/go/debian/control
github.com/cloudflare/circl/internal/conv
golang.org/x/crypto/sha3
github.com/go-git/go-billy/v5/osfs
github.com/cloudflare/circl/math/fp25519
github.com/cloudflare/circl/math/fp448
github.com/cloudflare/circl/math/mlsbset
github.com/go-git/go-billy/v5/util
github.com/cloudflare/circl/dh/x25519
github.com/cloudflare/circl/dh/x448
github.com/cloudflare/circl/sign/ed25519
github.com/cloudflare/circl/ecc/goldilocks
github.com/ProtonMail/go-crypto/openpgp/x25519
github.com/pjbgf/sha1cd
encoding/gob
github.com/ProtonMail/go-crypto/openpgp/ed25519
github.com/go-git/gcfg/token
github.com/ProtonMail/go-crypto/openpgp/x448
github.com/go-git/go-git/v5/plumbing/hash
github.com/go-git/go-git/v5/plumbing
github.com/go-git/gcfg/types
github.com/go-git/gcfg/scanner
gopkg.in/warnings.v0
github.com/go-git/go-git/v5/internal/path_util
github.com/go-git/go-git/v5/internal/revision
github.com/go-git/go-git/v5/plumbing/cache
net/http/httptrace
google.golang.org/grpc/internal/credentials
github.com/go-git/go-git/v5/plumbing/filemode
github.com/cloudflare/circl/sign/ed448
github.com/go-git/go-git/v5/utils/binary
net/http
golang.org/x/net/internal/httpcommon
github.com/go-git/go-git/v5/utils/sync
github.com/go-git/go-git/v5/plumbing/format/index
github.com/go-git/go-git/v5/plumbing/format/idxfile
google.golang.org/protobuf/internal/filetype
github.com/ProtonMail/go-crypto/openpgp/internal/ecc
github.com/ProtonMail/go-crypto/openpgp/ed448
github.com/emirpasic/gods/utils
github.com/go-git/go-git/v5/plumbing/format/diff
github.com/sergi/go-diff/diffmatchpatch
google.golang.org/protobuf/runtime/protoimpl
github.com/go-git/go-git/v5/plumbing/storer
github.com/emirpasic/gods/containers
github.com/ProtonMail/go-crypto/openpgp/ecdh
github.com/ProtonMail/go-crypto/openpgp/ecdsa
github.com/ProtonMail/go-crypto/openpgp/eddsa
github.com/emirpasic/gods/lists
google.golang.org/protobuf/types/descriptorpb
google.golang.org/protobuf/types/known/anypb
google.golang.org/protobuf/types/known/durationpb
google.golang.org/protobuf/types/known/timestamppb
github.com/ProtonMail/go-crypto/openpgp/packet
github.com/golang/protobuf/ptypes/any
google.golang.org/genproto/googleapis/rpc/status
github.com/golang/protobuf/ptypes/timestamp
github.com/go-git/go-git/v5/plumbing/format/packfile
 github.com/golang/protobuf/ptypes/duration
 github.com/emirpasic/gods/lists/arraylist
 github.com/emirpasic/gods/trees
 github.com/go-git/go-git/v5/utils/diff
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 github.com/go-git/gcfg
 github.com/go-git/go-git/v5/utils/trace
 github.com/emirpasic/gods/trees/binaryheap
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 github.com/go-git/go-git/v5/utils/merkletrie
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/kevinburke/ssh_config
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 github.com/go-git/go-git/v5/plumbing/format/config
 google.golang.org/protobuf/types/gofeaturespb
 crypto/mlkem
 golang.org/x/crypto/chacha20
 golang.org/x/crypto/curve25519
 google.golang.org/protobuf/reflect/protodesc
 golang.org/x/crypto/internal/poly1305
 github.com/go-git/go-git/v5/plumbing/format/objfile
 golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 golang.org/x/net/internal/socks
 golang.org/x/crypto/ssh
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 github.com/go-git/go-git/v5/utils/merkletrie/index
 github.com/docker-library/bashbrew/pkg/tarscrub
 github.com/docker-library/bashbrew/pkg/templatelib
 flag
 golang.org/x/net/proxy
 github.com/go-git/go-git/v5/storage
 github.com/go-git/go-git/v5/storage/memory
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 github.com/russross/blackfriday/v2
 github.com/ProtonMail/go-crypto/openpgp
 github.com/golang/protobuf/proto
 golang.org/x/term
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 github.com/go-git/go-git/v5/storage/filesystem
 github.com/go-git/go-git/v5/plumbing/transport
 github.com/go-git/go-git/v5/plumbing/object
 github.com/cpuguy83/go-md2man/v2/md2man
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 github.com/urfave/cli
 github.com/go-git/go-git/v5/plumbing/transport/git
 google.golang.org/grpc/credentials
 github.com/golang/protobuf/jsonpb
 google.golang.org/grpc/encoding/proto
 github.com/golang/protobuf/ptypes
 google.golang.org/grpc/binarylog/grpc_binarylog_v1
 google.golang.org/grpc/internal/channelz
google.golang.org/grpc/credentials/insecure
 google.golang.org/grpc/internal/status
 google.golang.org/grpc/peer
 github.com/go-git/go-git/v5/plumbing/revlist
 github.com/go-git/go-git/v5/plumbing/transport/server
 google.golang.org/grpc/status
 google.golang.org/grpc/channelz
 google.golang.org/grpc/internal/binarylog
 github.com/containerd/containerd/errdefs
 github.com/containerd/ttrpc
 github.com/go-git/go-git/v5/plumbing/transport/file
 google.golang.org/grpc/internal/pretty
 google.golang.org/grpc/resolver
 github.com/containerd/containerd/labels
 github.com/containerd/containerd/filters
 github.com/containerd/containerd/platforms
 google.golang.org/grpc/internal
 google.golang.org/grpc/internal/metadata
 google.golang.org/grpc/balancer
 google.golang.org/grpc/balancer/grpclb/state
 google.golang.org/grpc/internal/resolver/passthrough
 google.golang.org/grpc/internal/transport/networktype
 google.golang.org/grpc/internal/resolver/dns
 google.golang.org/grpc/internal/resolver/unix
 google.golang.org/grpc/balancer/base
 google.golang.org/grpc/internal/serviceconfig
 github.com/containerd/containerd/content
 google.golang.org/grpc/balancer/roundrobin
 google.golang.org/grpc/internal/balancer/gracefulswitch
 github.com/containerd/containerd/identifiers
 google.golang.org/grpc/internal/resolver
 github.com/docker-library/bashbrew/architecture
 golang.org/x/crypto/ssh/knownhosts
 github.com/containerd/containerd/namespaces
 golang.org/x/crypto/ssh/agent
 github.com/containerd/containerd/events/exchange
 github.com/containerd/containerd/content/local
 github.com/containerd/containerd/images
 github.com/containerd/containerd/plugin
 github.com/skeema/knownhosts
 github.com/containerd/containerd/images/archive
 github.com/containerd/containerd/oci
 github.com/containerd/containerd/diff
 github.com/containerd/containerd/remotes
 github.com/containerd/containerd/metadata
 github.com/xanzy/ssh-agent
 github.com/containerd/containerd/rootfs
 github.com/go-git/go-git/v5/plumbing/transport/ssh
 golang.org/x/net/trace
 golang.org/x/net/http2
 net/http/httputil
 github.com/containerd/containerd/remotes/errors
 golang.org/x/net/context/ctxhttp
 github.com/containerd/containerd/remotes/docker/schema1
 github.com/docker-library/bashbrew/manifest
 github.com/containerd/containerd/remotes/docker/auth
github.com/go-git/go-git/v5/plumbing/transport/http
 github.com/containerd/containerd/remotes/docker
 github.com/go-git/go-git/v5/plumbing/transport/client
 github.com/go-git/go-git/v5
 github.com/docker-library/bashbrew/registry
 google.golang.org/grpc/internal/transport
 github.com/docker-library/bashbrew/pkg/gitfs
 google.golang.org/grpc
 github.com/containerd/containerd/api/services/containers/v1
 github.com/containerd/containerd/api/services/diff/v1
 github.com/containerd/containerd/api/services/content/v1
 github.com/containerd/containerd/api/services/events/v1
 github.com/containerd/containerd/api/services/introspection/v1
 github.com/containerd/containerd/api/services/images/v1
 github.com/containerd/containerd/api/services/leases/v1
 github.com/containerd/containerd/api/services/namespaces/v1
 github.com/containerd/containerd/api/services/snapshots/v1
 github.com/containerd/containerd/api/services/tasks/v1
 github.com/containerd/containerd/api/services/version/v1
 github.com/containerd/containerd/services/introspection
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/leases/proxy
 github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-s390x
 -rwxr-xr-x 1 root root 22M 14 de marzo 01:02 bin/bashbrew-s390x*
 + archivo bin/bashbrew-s390x
 bin/bashbrew-s390x: ejecutable ELF de 64 bits MSB, IBM S/390, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=e58bde069af32fc0f18c911aa4cb6d6000e60108, eliminado
 + para bashbrewArch en $BASHBREW_ARCHES
 ++ bashbrew-arch-to-goenv.sh windows-amd64
 + goEnv='export GOARCH=amd64 GOAMD64=v1 GOOS=windows
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOPPC64'
 + eval 'export GOARCH=amd64 GOAMD64=v1 GOOS=windows
 unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOPPC64'
 ++ export GOARCH=amd64 GOAMD64=v1 GOOS=windows
 ++ GOARCH=amd64
 ++ GOAMD64=v1
 ++ GOOS=windows
 ++ unset GO386 GOARM GOMIPS64 GOARM64 GORISCV64 GOPPC64
 + '[' windows = windows ']'
 + ext=.exe
 + LDFLAGS='-s -w'
 + case "$GOOS" in
 + targetBin=bin/bashbrew-windows-amd64.exe
 + go build -v -ldflags '-s -w' -tags netgo -installsuffix netgo -o bin/bashbrew-windows-amd64.exe ./cmd/bashbrew
 internal/goos
 internal/unsafeheader
 internal/coverage/rtcov
 internal/godebugs
internal/goexperiment
internal/goarch
internal/byteorder
internal/profilerecord
internal/cpu
internal/abi
internal/asan
internal/runtime/atomic
internal/msan
internal/runtime/math
internal/runtime/sys
internal/chacha8rand
sync/atomic
math/bits
unicode
unicode/utf8
internal/syscall/windows/sysdll
internal/bytealg
internal/runtime/exithook
internal/itoa
unicode/utf16
math
crypto/internal/fips140/alias
crypto/internal/fips140deps/byteorder
crypto/internal/fips140deps/cpu
cmp
crypto/internal/fips140/subtle
crypto/internal/boring/sig
encoding
log/internal
internal/nettrace
container/list
vendor/golang.org/x/crypto/cryptobyte/asn1
vendor/golang.org/x/crypto/internal/alias
internal/stringslite
google.golang.org/protobuf/internal/flags
google.golang.org/protobuf/internal/set
google.golang.org/grpc/serviceconfig
github.com/golang/groupcache/lru
go.opencensus.io
google.golang.org/grpc/attributes
go.opencensus.io/trace/internal
github.com/Microsoft/hcsshim/internal/logfields
github.com/containerd/containerd/pkg/userns
github.com/klauspost/compress/internal/cpuinfo
github.com/klauspost/compress/internal/le
github.com/containerd/containerd/services
image/color
github.com/ProtonMail/go-crypto/internal/byteutil
golang.org/x/crypto/cryptobyte/asn1
github.com/pjbgf/sha1cd/internal
github.com/pjbgf/sha1cd/ubc
github.com/go-git/go-git/v5/plumbing/color
golang.org/x/crypto/internal/alias
internal/race
internal/sync
internal/runtime/maps
github.com/klauspost/compress
runtime
internal/reflectlite
iter
weak
github.com/containerd/containerd/version
crypto/subtle
sync
slices
maps
errors
sort
internal/bisect
internal/singleflight
internal/testlog
unique
google.golang.org/protobuf/internal/pragma
google.golang.org/grpc/internal/buffer
google.golang.org/grpc/internal/grpcsync
github.com/Microsoft/go-winio/internal/stringbuffer
io
internal/oserror
path
strconv
syscall
math/rand/v2
internal/godebug
vendor/golang.org/x/net/dns/dnsmessage
github.com/Microsoft/hcsshim/internal/queue
bytes
strings
hash
crypto/internal/randutil
github.com/gogo/protobuf/sortkeys
hash/crc32
internal/saferio
hash/fnv
crypto/internal/fips140deps/godebug
math/rand
github.com/moby/locker
crypto
reflect
net/netip
bufio
crypto/internal/fips140
crypto/internal/impl
html
regexp/syntax
crypto/internal/fips140/sha256
crypto/internal/fips140/sha3
crypto/internal/fips140/sha512
internal/syscall/windows
internal/syscall/windows/registry
crypto/sha3
crypto/tls/internal/fips140tls
vendor/golang.org/x/text/transform
crypto/internal/fips140hash
net/http/internal/ascii
golang.org/x/text/transform
github.com/opencontainers/selinux/go-selinux
time
crypto/internal/fips140/hmac
github.com/docker-library/bashbrew/pkg/stripper
golang.org/x/crypto/openpgp/errors
crypto/internal/fips140/check
compress/bzip2
regexp
hash/adler32
internal/syscall/execenv
crypto/internal/fips140/aes
crypto/internal/fips140/nistec/fiat
crypto/internal/fips140/edwards25519/field
crypto/internal/fips140/bigmod
crypto/internal/fips140/hkdf
crypto/internal/fips140/tls12
crypto/internal/fips140/tls13
golang.org/x/crypto/cast5
crypto/internal/fips140/edwards25519
golang.org/x/crypto/openpgp/s2k
image
pault.ag/go/topsort
github.com/docker-library/bashbrew/pkg/dockerfile
container/heap
github.com/cloudflare/circl/sign
github.com/cloudflare/circl/internal/sha3
crypto/fips140
github.com/go-git/go-git/v5/internal/url
golang.org/x/crypto/blowfish
google.golang.org/grpc/internal/grpcrand
io/fs
internal/poll
google.golang.org/grpc/backoff
context
google.golang.org/grpc/keepalive
image/internal/imageutil
google.golang.org/grpc/internal/backoff
image/jpeg
google.golang.org/grpc/tap
golang.org/x/sync/semaphore
github.com/containerd/containerd/gc
internal/filepathlite
crypto/internal/fips140/nistec
embed
golang.org/x/net/context
github.com/jbenet/go-context/io
google.golang.org/protobuf/internal/editiondefaults
github.com/go-git/go-git/v5/utils/ioutil
 os
 internal/fmtsort
 encoding/binary
 vendor/golang.org/x/crypto/internal/poly1305
 encoding/base64
 github.com/klauspost/compress/internal/snapref
 github.com/klauspost/compress/zstd/internal/xxhash
 golang.org/x/crypto/internal/poly1305
 encoding/pem
 golang.org/x/crypto/openpgp/armor
 fmt
 path/filepath
 vendor/golang.org/x/sys/cpu
 crypto/internal/sysrand
 io/ioutil
 net
 google.golang.org/protobuf/internal/detrand
 google.golang.org/grpc/internal/envconfig
 crypto/internal/entropy
 github.com/Microsoft/hcsshim/internal/timeout
 github.com/moby/sys/mountinfo
 github.com/containerd/fifo
 os/signal
 crypto/internal/fips140/drbg
 pault.ag/go/debian/internal
 golang.org/x/sys/cpu
 github.com/go-git/go-billy/v5
 github.com/Microsoft/hcsshim/internal/longpath
 os/exec
 crypto/internal/fips140/aes/gcm
 crypto/internal/fips140only
 crypto/internal/fips140/ecdh
 crypto/internal/fips140/ecdsa
 crypto/internal/fips140/ed25519
 crypto/internal/fips140/mlkem
 crypto/md5
 crypto/rc4
 crypto/internal/fips140/rsa
 crypto/cipher
 github.com/containerd/containerd/defaults
 github.com/docker-library/bashbrew/pkg/execpipe
 golang.org/x/crypto/blake2b
 golang.org/x/crypto/sha3
 github.com/cyphar/filepath-securejoin
 github.com/go-git/go-billy/v5/helper/polyfill
 github.com/go-git/go-billy/v5/util
 github.com/go-git/go-billy/v5/helper/chroot
 crypto/internal/boring
 crypto/des
 encoding/hex
 encoding/json
 crypto/sha256
 crypto/sha512
 archive/tar
 log
 compress/flate
 net/url
 text/template/parse
 math/big
 golang.org/x/net/internal/timeseries
 crypto/aes
 crypto/ecdh
 compress/gzip
 crypto/hmac
 vendor/golang.org/x/crypto/chacha20
 crypto/sha1
 vendor/golang.org/x/text/unicode/bidi
 text/template
 vendor/golang.org/x/text/unicode/norm
 vendor/golang.org/x/crypto/chacha20poly1305
 vendor/golang.org/x/net/http2/hpack
 mime
 vendor/golang.org/x/text/secure/bidirule
 mime/quotedprintable
 net/http/internal
 crypto/rand
 crypto/elliptic
 github.com/gogo/protobuf/proto
crypto/internal/boring/bbig
encoding/asn1
crypto/ed25519
crypto/internal/hpke
crypto/rsa
crypto/dsa
net/textproto
text/tabwriter
google.golang.org/grpc/internal/grpclog
html/template
google.golang.org/grpc/grpclog
google.golang.org/protobuf/internal/errors
mime/multipart
go/token
google.golang.org/protobuf/encoding/protowire
google.golang.org/grpc/connectivity
google.golang.org/protobuf/reflect/protoreflect
vendor/golang.org/x/net/idna
google.golang.org/protobuf/internal/version
google.golang.org/grpc/metadata
google.golang.org/grpc/codes
vendor/golang.org/x/crypto/cryptobyte
crypto/x509/pkix
google.golang.org/grpc/internal/grpcutil
google.golang.org/grpc/internal/balancerload
golang.org/x/text/unicode/bidi
google.golang.org/grpc/encoding
golang.org/x/text/unicode/norm
golang.org/x/net/http2/hpack
google.golang.org/grpc/internal/syscall
vendor/golang.org/x/net/http/httpguts
crypto/ecdsa
vendor/golang.org/x/net/http/httpproxy
google.golang.org/protobuf/internal/encoding/messageset
google.golang.org/protobuf/internal/strs
google.golang.org/protobuf/internal/genid
google.golang.org/protobuf/internal/order
google.golang.org/protobuf/reflect/protoregistry
google.golang.org/protobuf/runtime/protoiface
google.golang.org/protobuf/internal/descfmt
google.golang.org/protobuf/internal/encoding/text
google.golang.org/protobuf/internal/descopts
google.golang.org/protobuf/internal/encoding/json
golang.org/x/text/secure/bidirule
google.golang.org/grpc/stats
google.golang.org/protobuf/proto
github.com/opencontainers/go-digest
google.golang.org/protobuf/internal/encoding/defval
github.com/pkg/errors
golang.org/x/sys/windows
crypto/x509
go.opencensus.io/internal
go.opencensus.io/trace/tracestate
runtime/trace
github.com/Microsoft/hcsshim/internal/hcserror
github.com/Microsoft/hcsshim/internal/mergemaps
golang.org/x/sync/errgroup
github.com/klauspost/compress/fse
go.opencensus.io/trace
golang.org/x/net/idna
runtime/debug
google.golang.org/protobuf/encoding/prototext
google.golang.org/protobuf/internal/filedesc
github.com/klauspost/compress/huff0
golang.org/x/sys/execabs
github.com/opencontainers/image-spec/specs-go
github.com/opencontainers/image-spec/specs-go/v1
github.com/containerd/containerd/reference
github.com/containerd/containerd/reference/docker
github.com/containerd/containerd/leases
golang.org/x/net/http/httpguts
github.com/opencontainers/runc/libcontainer/user
github.com/opencontainers/runtime-spec/specs-go
github.com/containerd/containerd/pkg/kmutex
github.com/opencontainers/image-spec/identity
github.com/klauspost/compress/zstd
database/sql/driver
github.com/opencontainers/selinux/go-selinux/label
compress/zlib
golang.org/x/crypto/openpgp/elgamal
pault.ag/go/debian/version
golang.org/x/crypto/openpgp/packet
github.com/google/uuid
pault.ag/go/debian/dependency
crypto/tls
google.golang.org/protobuf/internal/encoding/tag
google.golang.org/protobuf/encoding/protojson
pault.ag/go/debian/hashio
google.golang.org/protobuf/internal/impl
dario.cat/mergo
github.com/gogo/protobuf/types
github.com/gogo/protobuf/protoc-gen-gogo/descriptor
github.com/containerd/containerd/runtime/linux/runctypes
github.com/containerd/containerd/runtime/v2/runc/options
golang.org/x/crypto/openpgp
golang.org/x/crypto/openpgp/clearsign
github.com/ProtonMail/go-crypto/openpgp/errors
github.com/ProtonMail/go-crypto/openpgp/armor
github.com/ProtonMail/go-crypto/openpgp/aes/keywrap
github.com/gogo/protobuf/gogoproto
pault.ag/go/debian/control
github.com/ProtonMail/go-crypto/eax
github.com/ProtonMail/go-crypto/ocb
github.com/containerd/cgroups/stats/v1
github.com/ProtonMail/go-crypto/openpgp/internal/algorithm
github.com/ProtonMail/go-crypto/bitcurves
github.com/ProtonMail/go-crypto/brainpool
github.com/ProtonMail/go-crypto/openpgp/internal/encoding
golang.org/x/crypto/cryptobyte
github.com/cloudflare/circl/math
github.com/ProtonMail/go-crypto/openpgp/elgamal
golang.org/x/crypto/argon2
golang.org/x/crypto/hkdf
github.com/pjbgf/sha1cd
github.com/Microsoft/go-winio/internal/fs
github.com/Microsoft/go-winio/pkg/guid
github.com/Microsoft/go-winio/pkg/security
github.com/Microsoft/hcsshim/internal/interop
github.com/sirupsen/logrus
github.com/Microsoft/hcsshim/osversion
github.com/Microsoft/go-winio/internal/socket
github.com/Microsoft/go-winio/vhd
github.com/Microsoft/hcsshim/internal/winapi
github.com/moby/sys/signal
go.etcd.io/bbolt
github.com/Microsoft/go-winio
github.com/cloudflare/circl/internal/conv
github.com/ProtonMail/go-crypto/openpgp/s2k
github.com/cloudflare/circl/math/fp25519
github.com/cloudflare/circl/math/fp448
github.com/containerd/containerd/api/types
github.com/containerd/typeurl
github.com/gogo/googleapis/google/rpc
net/http/httptrace
google.golang.org/grpc/internal/credentials
github.com/containerd/containerd/api/types/task
github.com/Microsoft/go-winio/backuptar
github.com/Microsoft/hcsshim/internal/oc
net/http
golang.org/x/net/internal/httpcommon
github.com/Microsoft/hcsshim/internal/log
github.com/Microsoft/hcsshim/internal/jobobject
github.com/Microsoft/hcsshim/internal/vmcompute
github.com/Microsoft/hcsshim/internal/hns
github.com/Microsoft/hcsshim/internal/safefile
github.com/containerd/containerd/log
github.com/containerd/continuity/fs
github.com/Microsoft/hcsshim/internal/wclayer
google.golang.org/protobuf/internal/filetype
github.com/containerd/containerd/archive/compression
github.com/containerd/containerd/cio
google.golang.org/protobuf/runtime/protoimpl
github.com/containerd/containerd/containers
github.com/containerd/containerd/events
github.com/containerd/containerd/pkg/dialer
github.com/docker/go-events
github.com/containerd/containerd/metadata/boltutil
github.com/cloudflare/circl/dh/x25519
google.golang.org/protobuf/types/descriptorpb
google.golang.org/protobuf/types/known/anypb
google.golang.org/protobuf/types/known/durationpb
google.golang.org/protobuf/types/known/timestamppb
github.com/cloudflare/circl/dh/x448
github.com/golang/protobuf/ptypes/any
google.golang.org/genproto/googleapis/rpc/status
github.com/golang/protobuf/ptypes/timestamp
github.com/golang/protobuf/ptypes/duration
github.com/cloudflare/circl/sign/ed25519
github.com/cloudflare/circl/math/mlsbset
github.com/ProtonMail/go-crypto/openpgp/x25519
github.com/go-git/go-billy/v5/osfs
github.com/go-git/go-git/v5/plumbing/hash
encoding/gob
github.com/cloudflare/circl/ecc/goldilocks
github.com/go-git/go-git/v5/plumbing
github.com/ProtonMail/go-crypto/openpgp/ed25519
github.com/go-git/gcfg/token
github.com/ProtonMail/go-crypto/openpgp/x448
github.com/go-git/gcfg/types
gopkg.in/warnings.v0
github.com/go-git/gcfg/scanner
os/user
github.com/go-git/go-git/v5/internal/revision
 github.com/go-git/go-git/v5/plumbing/cache
 github.com/go-git/go-git/v5/plumbing/filemode
 google.golang.org/protobuf/types/gofeaturespb
 github.com/cloudflare/circl/sign/ed448
 github.com/go-git/go-git/v5/utils/binary
 github.com/go-git/go-git/v5/utils/sync
 github.com/go-git/go-git/v5/internal/path_util
 github.com/emirpasic/gods/utils
 github.com/go-git/go-git/v5/plumbing/format/index
 github.com/go-git/go-git/v5/plumbing/format/idxfile
 google.golang.org/protobuf/reflect/protodesc
 github.com/go-git/go-git/v5/plumbing/format/diff
 github.com/emirpasic/gods/containers
 github.com/ProtonMail/go-crypto/openpgp/internal/ecc
 github.com/ProtonMail/go-crypto/openpgp/ed448
 github.com/emirpasic/gods/lists
 github.com/emirpasic/gods/trees
 github.com/sergi/go-diff/diffmatchpatch
 github.com/ProtonMail/go-crypto/openpgp/ecdh
 github.com/ProtonMail/go-crypto/openpgp/ecdsa
 github.com/ProtonMail/go-crypto/openpgp/eddsa
 github.com/go-git/go-git/v5/plumbing/storer
 github.com/emirpasic/gods/lists/arraylist
 github.com/go-git/go-git/v5/utils/merkletrie/noder
 github.com/ProtonMail/go-crypto/openpgp/packet
 github.com/go-git/go-git/v5/utils/merkletrie/internal/frame
 github.com/emirpasic/gods/trees/binaryheap
 github.com/go-git/go-git/v5/plumbing/format/packfile
 github.com/go-git/go-git/v5/utils/merkletrie
 github.com/go-git/go-git/v5/utils/trace
 github.com/go-git/go-git/v5/plumbing/protocol/packp/capability
 github.com/go-git/go-git/v5/utils/diff
 github.com/go-git/go-git/v5/plumbing/format/pktline
 github.com/kevinburke/ssh_config
 crypto/mlkem
 github.com/go-git/gcfg
 github.com/go-git/go-git/v5/plumbing/protocol/packp/sideband
 github.com/golang/protobuf/proto
 golang.org/x/crypto/chacha20
 golang.org/x/crypto/curve25519
 golang.org/x/crypto/ssh/internal/bcrypt_pbkdf
 golang.org/x/net/internal/socks
 golang.org/x/crypto/ssh
 github.com/go-git/go-git/v5/utils/merkletrie/filesystem
 github.com/go-git/go-git/v5/plumbing/format/config
 golang.org/x/net/proxy
 github.com/go-git/go-git/v5/utils/merkletrie/index
 github.com/go-git/go-git/v5/plumbing/format/objfile
 github.com/docker-library/bashbrew/pkg/tarscrub
 github.com/go-git/go-git/v5/config
 github.com/go-git/go-git/v5/plumbing/format/gitignore
 github.com/docker-library/bashbrew/pkg/templatelib
 flag
github.com/russross/blackfriday/v2
 golang.org/x/term
 github.com/go-git/go-git/v5/storage
 github.com/go-git/go-git/v5/storage/memory
 google.golang.org/grpc/credentials
 github.com/golang/protobuf/jsonpb
 google.golang.org/grpc/encoding/proto
 github.com/golang/protobuf/ptypes
 google.golang.org/grpc/binarylog/grpc_binarylog_v1
 github.com/ProtonMail/go-crypto/openpgp
 google.golang.org/grpc/internal/channelz
 google.golang.org/grpc/credentials/insecure
 google.golang.org/grpc/internal/status
 google.golang.org/grpc/peer
 github.com/go-git/go-git/v5/plumbing/protocol/packp
 google.golang.org/grpc/status
 google.golang.org/grpc/internal/pretty
 google.golang.org/grpc/resolver
 github.com/go-git/go-git/v5/storage/filesystem/dotgit
 google.golang.org/grpc/internal/binarylog
 google.golang.org/grpc/internal
 google.golang.org/grpc/channelz
 google.golang.org/grpc/internal/metadata
 google.golang.org/grpc/balancer
 google.golang.org/grpc/balancer/grpclb/state
 google.golang.org/grpc/internal/resolver/passthrough
 google.golang.org/grpc/internal/resolver/dns
 google.golang.org/grpc/internal/transport/networktype
 google.golang.org/grpc/balancer/base
 google.golang.org/grpc/internal/serviceconfig
 google.golang.org/grpc/internal/resolver
 google.golang.org/grpc/internal/resolver/unix
 github.com/containerd/containerd/errdefs
 google.golang.org/grpc/balancer/roundrobin
 google.golang.org/grpc/internal/balancer/gracefulswitch
 github.com/containerd/ttrpc
 github.com/go-git/go-git/v5/plumbing/transport
 github.com/go-git/go-git/v5/plumbing/object
 github.com/containerd/containerd/filters
 github.com/containerd/containerd/labels
 github.com/containerd/containerd/platforms
 github.com/containerd/containerd/identifiers
 github.com/go-git/go-git/v5/plumbing/transport/internal/common
 github.com/go-git/go-git/v5/storage/filesystem
 github.com/containerd/containerd/content
 github.com/go-git/go-git/v5/plumbing/transport/git
 github.com/docker-library/bashbrew/architecture
 golang.org/x/net/trace
 golang.org/x/net/http2
 net/http/httputil
 github.com/Microsoft/hcsshim/internal/hcs/schema2
 github.com/containerd/containerd/images
 github.com/containerd/containerd/namespaces
 github.com/Microsoft/hcsshim/computestorage
 github.com/Microsoft/hcsshim/internal/hcs/schema1
github.com/containerd/containerd/events/exchange
github.com/Microsoft/hcsshim/internal/cow
github.com/containerd/containerd/images/archive
github.com/containerd/containerd/remotes
github.com/containerd/containerd/remotes/errors
github.com/Microsoft/hcsshim/internal/hcs
github.com/containerd/containerd/plugin
golang.org/x/net/context/ctxhttp
github.com/containerd/containerd/remotes/docker/auth
github.com/containerd/containerd/content/local
github.com/docker-library/bashbrew/manifest
github.com/go-git/go-git/v5/plumbing/revlist
github.com/go-git/go-git/v5/plumbing/transport/http
github.com/containerd/containerd/remotes/docker/schema1
golang.org/x/crypto/ssh/knownhosts
github.com/go-git/go-git/v5/plumbing/transport/server
github.com/skeema/knownhosts
golang.org/x/crypto/ssh/agent
github.com/go-git/go-git/v5/plumbing/transport/file
github.com/containerd/containerd/remotes/docker
github.com/Microsoft/hcsshim
github.com/cpuguy83/go-md2man/v2/md2man
github.com/urfave/cli
github.com/containerd/containerd/sys
github.com/containerd/containerd/mount
github.com/Microsoft/hcsshim/pkg/ociwclayer
github.com/xanzy/ssh-agent
github.com/containerd/containerd/diff
github.com/containerd/containerd/snapshots
github.com/containerd/containerd/archive
github.com/go-git/go-git/v5/plumbing/transport/ssh
github.com/containerd/containerd/oci
github.com/containerd/containerd/metadata
github.com/docker-library/bashbrew/registry
github.com/containerd/containerd/rootfs
github.com/go-git/go-git/v5/plumbing/transport/client
github.com/go-git/go-git/v5
google.golang.org/grpc/internal/transport
github.com/docker-library/bashbrew/pkg/gitfs
google.golang.org/grpc
github.com/containerd/containerd/api/services/containers/v1
github.com/containerd/containerd/api/services/content/v1
github.com/containerd/containerd/api/services/events/v1
github.com/containerd/containerd/api/services/introspection/v1
github.com/containerd/containerd/api/services/namespaces/v1
github.com/containerd/containerd/api/services/images/v1
github.com/containerd/containerd/api/services/diff/v1
github.com/containerd/containerd/api/services/leases/v1
github.com/containerd/containerd/api/services/snapshots/v1
github.com/containerd/containerd/api/services/tasks/v1
github.com/containerd/containerd/api/services/version/v1
github.com/containerd/containerd/leases/proxy
 github.com/containerd/containerd/services/introspection
 google.golang.org/grpc/health/grpc_health_v1
 github.com/containerd/containerd/content/proxy
 github.com/containerd/containerd/snapshots/proxy
 github.com/containerd/containerd
 github.com/docker-library/bashbrew/cmd/bashbrew
 + ls -lAFh bin/bashbrew-windows-amd64.exe
 -rwxr-xr-x 1 root root 22M 14 de marzo 01:03 bin/bashbrew-windows-amd64.exe*
 + archivo bin/bashbrew-windows-amd64.exe
 bin/bashbrew-windows-amd64.exe: ejecutable PE32+ para MS Windows 6.01 (consola), x86-64, 8 secciones
 + ls -lAFh bin/bashbrew-amd64 bin/bashbrew-arm32v5 bin/bashbrew-arm32v6 bin/bashbrew-arm32v7 bin/bashbrew-arm64v8 bin/bashbrew-darwin-amd64 bin/bashbrew-i386 bin/bashbrew-mips64le bin/bashbrew-ppc64le bin/bashbrew-riscv64 bin/bashbrew-s390x bin/bashbrew-windows-amd64.exe
 -rwxr-xr-x 1 root root 21M 14 de marzo 00:55 bin/bashbrew-amd64*
-rwxr-xr-x 1 root root 20M 14 de marzo 00:55 bin/bashbrew-arm32v5*
-rwxr-xr-x 1 root root 20M 14 de marzo 00:56 bin/bashbrew-arm32v6*
-rwxr-xr-x 1 root root 20M 14 de marzo 00:56 bin/bashbrew-arm32v7*
-rwxr-xr-x 1 raíz raíz 19M 14 de marzo 00:57 bin/bashbrew-arm64v8*
-rwxr-xr-x 1 root root 21M 14 de marzo 00:57 bin/bashbrew-darwin-amd64*
-rwxr-xr-x 1 root root 20M 14 de marzo 00:58 bin/bashbrew-i386*
-rwxr-xr-x 1 root root 23M 14 de marzo 00:59 bin/bashbrew-mips64le*
-rwxr-xr-x 1 raíz raíz 20M 14 de marzo 01:00 bin/bashbrew-ppc64le*
-rwxr-xr-x 1 root root 20M 14 de marzo 01:01 bin/bashbrew-riscv64*
-rwxr-xr-x 1 root root 22M 14 de marzo 01:02 bin/bashbrew-s390x*
-rwxr-xr-x 1 root root 22M 14 de marzo 01:03 bin/bashbrew-windows-amd64.exe*
+ archivo bin/bashbrew-amd64 bin/bashbrew-arm32v5 bin/bashbrew-arm32v6 bin/bashbrew-arm32v7 bin/bashbrew-arm64v8 bin/bashbrew-darwin-amd64 bin/bashbrew-i386 bin/bashbrew-mips64le bin/bashbrew-ppc64le bin/bashbrew-riscv64 bin/bashbrew-s390x bin/bashbrew-windows-amd64.exe
 bin/bashbrew-amd64: ejecutable ELF de 64 bits LSB, x86-64, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=b87a33abac5639cea553f5642515264cf5476208, sin símbolos de depuración
bin/bashbrew-arm32v5: ejecutable ELF de 32 bits LSB, ARM, versión EABI5 1 (SYSV), enlazado estáticamente, BuildID[sha1]=572038e875e102f4cc39e0ad1d7150560729f310, sin símbolos de depuración
bin/bashbrew-arm32v6: ejecutable ELF de 32 bits LSB, ARM, versión EABI5 1 (SYSV), enlazado estáticamente, BuildID[sha1]=90996b8986bd78adb00a1ba1ed3bb241d81f5c2b, sin símbolos de depuración
bin/bashbrew-arm32v7: ejecutable ELF de 32 bits LSB, ARM, versión EABI5 1 (SYSV), enlazado estáticamente, BuildID[sha1]=aa35bdb3583aaa257c1930f31f72f859afaedde6, sin símbolos de depuración
bin/bashbrew-arm64v8: ejecutable ELF de 64 bits LSB, ARM aarch64, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=f7c42e0a6d03dbefe7d8ceed229860312bc01567, sin símbolos de depuración
bin/bashbrew-darwin-amd64: ejecutable Mach-O de 64 bits x86_64, flags:<|DYLDLINK|PIE>
bin/bashbrew-i386: ejecutable ELF de 32 bits LSB, Intel i386, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=22c71ac96ada8579d3d2e427c665db5181c3c101, sin símbolos de depuración
bin/bashbrew-mips64le: ejecutable ELF de 64 bits LSB, MIPS, MIPS-III versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=92b93d7dde800560eb3f6863e16e64a9b2d32cf5, sin símbolos de depuración
bin/bashbrew-ppc64le: ejecutable ELF de 64 bits LSB, PowerPC o Cisco 7500 de 64 bits, ABI OpenPOWER ELF V2, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=6449f3c37f50c43272d3d6e2f3df3450706060e1, sin símbolos de depuración
bin/bashbrew-riscv64: ejecutable ELF de 64 bits LSB, UCB RISC-V, ABI de doble punto flotante, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=c4adfb02272eddffb4e2d49936853dd81af8e9e0, sin símbolos de depuración
bin/bashbrew-s390x: ejecutable ELF de 64 bits MSB, IBM S/390, versión 1 (SYSV), enlazado estáticamente, BuildID[sha1]=e58bde069af32fc0f18c911aa4cb6d6000e60108, sin símbolos de depuración
bin/bashbrew-windows-amd64.exe: ejecutable PE32+ para MS Windows 6.01 (consola), x86-64, 8 secciones
Eliminando el contenedor intermedio 60eb8b5e4e68
 ---> 1ce9569c9e2a
Se construyó con éxito 1ce9569c9e2a
Se ha etiquetado correctamente bashbrew:master
+ rm -rf bin
+ docker run -i --rm bashbrew:master tar -c bin
+ tar -xv
papelera/
bin/manifest-tool-arm32v6.asc
bin/manifest-tool-arm32v7.asc
bin/manifest-tool-windows-amd64.exe
bin/manifest-tool-amd64
bin/manifest-tool-ppc64le.asc
bin/manifest-tool-mips64le.asc
bin/manifest-tool-arm32v5
bin/manifest-tool-i386
bin/manifest-tool-arm64v8.asc
bin/manifest-tool-arm32v6
bin/manifest-tool-arm64v8
bin/manifest-tool-mips64le
bin/manifest-tool-s390x.asc
bin/manifest-tool-ppc64le
bin/manifest-tool-amd64.asc
bin/manifest-tool-darwin-amd64.asc
bin/manifest-tool-arm32v5.asc
bin/manifest-tool-windows-amd64.exe.asc
bin/manifest-tool-darwin-amd64
bin/manifest-tool-i386.asc
bin/manifest-tool-s390x
bin/manifest-tool-arm32v7
bin/bashbrew-windows-amd64.exe
bin/bashbrew-riscv64
bin/bashbrew-amd64
bin/bashbrew-darwin-amd64
bin/bashbrew-s390x
bin/bashbrew-arm32v7
bin/bashbrew-arm32v5
bin/bashbrew-ppc64le
bin/bashbrew-arm64v8
bin/bashbrew-arm32v6
bin/bashbrew-i386
bin/bashbrew-mips64le
[Pipeline] }
 [Pipeline] // etapa
 [Pipeline] }
[Pipeline] // ansiColor
 [Pipeline] dir 

Ejecutándose en /mnt/docker/jenkins/doi-janky/workspace/bashbrew_master/bashbrew/bin

[Pipeline] { 
 [Pipeline] stage 
 [Pipeline] { (Archivo) 
 [Pipeline] archiveArtifacts 

Archivo de artefactos

Registro de huellas dactilares

[Pipeline] }
 [Pipeline] // etapa
 [Pipeline] }
 [Pipeline] // directorio
 [Pipeline] }
 [Pipeline] // directorio
 [Pipeline] }
 [Pipeline] // nodo
 [Pipeline] Fin de Pipeline

Finalizado: ÉXITO
# GitHub Command Palette

Use the command palette to navigate, search, and run commands directly from your keyboard.

> \[!NOTE]
> The GitHub Command Palette is currently in public preview and is subject to change.

The GitHub Command Palette is deactivated by default. You can enable the GitHub Command Palette with feature preview. See [Exploring early access releases with feature preview](/en/get-started/using-github/exploring-early-access-releases-with-feature-preview).

## About the GitHub Command Palette

You can navigate, search, and run commands on GitHub with the GitHub Command Palette. The command palette is an on-demand way to show suggestions based on your current context and resources you've used recently. You can open the command palette with a keyboard shortcut from anywhere on GitHub, which saves you time and keeps your hands on the keyboard.

### Fast navigation

When you open the command palette, the suggestions are optimized to give you easy access from anywhere in a repository, personal account, or organization to top-level pages like the Issues page. If the location you want isn't listed, start entering the name or number for the location to refine the suggestions.

![Screenshot of the command palette. The "Issues" and "Pull requests" pages for the current repository are suggested.](/assets/images/help/command-palette/command-palette-navigation-repo-default.png)

### Easy access to commands

The ability to run commands directly from your keyboard, without navigating through a series of menus, may change the way you use GitHub. For example, you can switch themes with a few keystrokes, making it easy to toggle between themes as your needs change.

![Screenshot of the command palette. "switch theme to dark" is in the command palette input, and results for changing your theme are displayed.](/assets/images/help/command-palette/command-palette-command-change-theme.png)

## Opening the GitHub Command Palette

Open the command palette using one of the following default keyboard shortcuts:

* Windows and Linux: <kbd>Ctrl</kbd>+<kbd>K</kbd> or <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>K</kbd>
* Mac: <kbd>Command</kbd>+<kbd>K</kbd> or <kbd>Command</kbd>+<kbd>Option</kbd>+<kbd>K</kbd>

You can customize the keyboard shortcuts you use to open the command palette in the [Accessibility section](https://github.com/settings/accessibility) of your user settings. For more information, see [Customizing your GitHub Command Palette keyboard shortcuts](#customizing-your-github-command-palette-keyboard-shortcuts).

When you open the command palette, it shows your location at the top left and uses it as the scope for suggestions (for example, the `octo-org` organization).

![Screenshot of the command palette. "octo-org" is highlighted with an orange outline.](/assets/images/help/command-palette/command-palette-launch.png)

> \[!NOTE]
>
> * If you are editing Markdown text, open the command palette with <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>K</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Option</kbd>+<kbd>K</kbd> (Mac).
> * If you are working on a project, a project-specific command palette is displayed instead. For more information, see [Changing the layout of a view](/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/changing-the-layout-of-a-view).

### Customizing your GitHub Command Palette keyboard shortcuts

The default keyboard shortcuts used to open the command palette may conflict with your default OS and browser keyboard shortcuts. You have the option to customize your keyboard shortcuts in the [Accessibility section](https://github.com/settings/accessibility) of your account settings. In the command palette settings, you can customize the keyboard shortcuts for opening the command palette in both search mode and command mode.

## Navigating with the GitHub Command Palette

You can use the command palette to navigate to any page that you have access to on GitHub.

1. Use <kbd>Ctrl</kbd>+<kbd>K</kbd> (Windows/Linux) or <kbd>Command</kbd>+<kbd>K</kbd> (Mac) to open the command palette with a scope determined by your current location in the UI.

2. Start typing the path you want to navigate to. The suggestions in the command palette change to match your text.

3. Optionally, narrow, expand, or completely change the scope for suggestions by editing the path in the command palette's text field.

   * To narrow the scope within a user or organization account, highlight a repository then use <kbd>Tab</kbd> to add it to the scope.
   * To expand the scope, highlight and remove an item in the scope using the <kbd>Backspace</kbd> or <kbd>delete</kbd> key.
   * To clear the scope and text box, click **Clear** or use <kbd>Ctrl</kbd>+<kbd>Backspace</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Delete</kbd> (Mac).

   You can also use keystrokes to narrow your search. For more information, see [Keystroke functions](#keystroke-functions).

4. Finish entering the path, or use the arrow keys to highlight the path you want from the list of suggestions.

5. Use <kbd>Enter</kbd> to jump to your chosen location. Alternatively, use <kbd>Ctrl</kbd>+<kbd>Enter</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Enter</kbd> (Mac) to open the location in a new browser tab.

## Searching with the GitHub Command Palette

You can use the command palette to search for anything on GitHub.

1. Use <kbd>Ctrl</kbd>+<kbd>K</kbd> (Windows/Linux) or <kbd>Command</kbd>+<kbd>K</kbd> (Mac) to open the command palette with a scope determined by your current location in the UI.

2. Optionally, narrow, expand, or completely change the scope for suggestions by editing the path in the command palette's text field.

   * To narrow the scope within a user or organization account, highlight a repository then use <kbd>Tab</kbd> to add it to the scope.
   * To expand the scope, highlight and remove an item in the scope using the <kbd>Backspace</kbd> or <kbd>delete</kbd> key.
   * To clear the scope and text box, click **Clear** or use <kbd>Ctrl</kbd>+<kbd>Backspace</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Delete</kbd> (Mac).

3. Optionally, use keystrokes to find specific types of resource:

   * <kbd>#</kbd> Search for issues, pull requests, discussions, and projects
   * <kbd>!</kbd> Search for projects
   * <kbd>@</kbd> Search for users, organizations, and repositories
   * <kbd>/</kbd> Search for files within a repository scope

4. Begin entering your search terms. The command palette will offer you a range of suggested searches based on your search scope.

   > \[!TIP]
   > You can also use the full syntax of GitHub's integrated search within the command palette. For more information, see [Search on GitHub documentation](/en/search-github).

5. Use the arrow keys to highlight the search result you want and use <kbd>Enter</kbd> to jump to your chosen location. Alternatively, use <kbd>Ctrl</kbd>+<kbd>Enter</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Enter</kbd> (Mac) to open the location in a new browser tab.

## Running commands from the GitHub Command Palette

You can use the GitHub Command Palette to run commands. For example, you can create a new repository or issue, or change your theme. When you run a command, the location for its action is determined by either the underlying page or the scope shown in the command palette.

* Pull request and issue commands always run on the underlying page.
* Higher-level commands, for example, repository commands, run in the scope shown in the command palette.

For a full list of supported commands, see [GitHub Command Palette reference](#github-command-palette-reference).

1. The default keyboard shortcuts to open the command palette in command mode are <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>K</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>K</kbd> (Mac). If you already have the command palette open, press <kbd>></kbd> to switch to command mode. GitHub suggests commands based on your location.

2. Optionally, narrow, expand, or completely change the scope for suggestions by editing the path in the command palette's text field.

   * To narrow the scope within a user or organization account, highlight a repository then use <kbd>Tab</kbd> to add it to the scope.
   * To expand the scope, highlight and remove an item in the scope using the <kbd>Backspace</kbd> or <kbd>delete</kbd> key.
   * To clear the scope and text box, click **Clear** or use <kbd>Ctrl</kbd>+<kbd>Backspace</kbd> (Windows and Linux) or <kbd>Command</kbd>+<kbd>Delete</kbd> (Mac).

3. If the command you want is not displayed, check your scope then start entering the command name in the text box.

4. Use the arrow keys to highlight the command you want and use <kbd>Enter</kbd> to run it.

## Closing the command palette

When the command palette is active, you can use one of the following keyboard shortcuts to close the command palette:

* Search and navigation mode: <kbd>Esc</kbd> or <kbd>Ctrl</kbd>+<kbd>K</kbd> (Windows and Linux)  <kbd>Command</kbd>+<kbd>K</kbd> (Mac)
* Command mode: <kbd>Esc</kbd> or <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>K</kbd> (Windows and Linux)  <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>K</kbd> (Mac)

If you have customized the command palette keyboard shortcuts in the Accessibility settings, your customized keyboard shortcuts will be used for both opening and closing the command palette.

## GitHub Command Palette reference

### Keystroke functions

These keystrokes are available when the command palette is in navigation and search modes, that is, they are not available in command mode.

| Keystroke                                                               | Function                                                                                                                                                                                                    |
| :---------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <kbd>></kbd>                                                            | Enter command mode. For more information, see [Running commands from the GitHub Command Palette](#running-commands-from-the-github-command-palette).                                                        |
| <kbd>#</kbd>                                                            | Search for issues, pull requests, discussions, and projects. For more information, see [Searching with the GitHub Command Palette](#searching-with-the-github-command-palette).                             |
| <kbd>@</kbd>                                                            | Search for users, organizations, and repositories. For more information, see [Searching with the GitHub Command Palette](#searching-with-the-github-command-palette).                                       |
| <kbd>/</kbd>                                                            | Search for files within a repository scope or repositories within an organization scope. For more information, see [Searching with the GitHub Command Palette](#searching-with-the-github-command-palette). |
| <kbd>!</kbd>                                                            | Search just for projects. For more information, see [Searching with the GitHub Command Palette](#searching-with-the-github-command-palette).                                                                |
| <kbd>Ctrl</kbd>+<kbd>C</kbd> or <kbd>Command</kbd>+<kbd>C</kbd>         | Copy the search or navigation URL for the highlighted result to the clipboard.                                                                                                                              |
| <kbd>Enter</kbd>                                                        | Jump to the highlighted result or run the highlighted command.                                                                                                                                              |
| <kbd>Ctrl</kbd>+<kbd>Enter</kbd> or <kbd>Command</kbd>+<kbd>Enter</kbd> | Open the highlighted search or navigation result in a new browser tab.                                                                                                                                      |
| <kbd>?</kbd>                                                            | Display help within the command palette.                                                                                                                                                                    |

### Global commands

These commands are available from all scopes.

| Command                        | Behavior                                                                                                                                                                                                                                                             |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Import repository`            | Create a new repository by importing a project from another version control system. For more information, see [Importing a repository with GitHub Importer](/en/migrations/importing-source-code/using-github-importer/importing-a-repository-with-github-importer). |
| `New gist`                     | Open a new gist. For more information, see [Creating gists](/en/get-started/writing-on-github/editing-and-sharing-content-with-gists/creating-gists).                                                                                                                |
| `New organization`             | Create a new organization. For more information, see [Creating a new organization from scratch](/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch).                                                              |
| `New project`                  | Create a new project. For more information, see [Creating a project](/en/issues/planning-and-tracking-with-projects/creating-projects/creating-a-project).                                                                                                           |
| `New repository`               | Create a new repository from scratch. For more information, see [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository).                                                                                          |
| `Switch theme to <theme name>` | Change directly to a different theme for the UI. For more information, see [Managing your theme settings](/en/get-started/accessibility/managing-your-theme-settings).                                                                                               |

### Organization commands

These commands are available only within the scope of an organization.

| Command    | Behavior                                                                                                                                                                   |
| :--------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `New team` | Create a new team in the current organization. For more information, see [Creating an organization team](/en/organizations/organizing-members-into-teams/creating-a-team). |

### Repository commands

Most of these commands are available only on the home page of the repository. If a command is also available on other pages, this is noted in the behavior column.

| Command                        | Behavior                                                                                                                                                                                                                  |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Clone repository: <URL type>` | Copy the URL needed to clone the repository using GitHub CLI, HTTPS, or SSH to the clipboard. For more information, see [Cloning a repository](/en/repositories/creating-and-managing-repositories/cloning-a-repository). |
| `New discussion`               | Create a new discussion in the repository. For more information, see [Quickstart for GitHub Discussions](/en/discussions/quickstart#creating-a-new-discussion).                                                           |
| `New file`                     | Create a new file from any page in the repository. For more information, see [Adding a file to a repository](/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository).                           |
| `New issue`                    | Open a new issue from any page in the repository. For more information, see [Creating an issue](/en/issues/tracking-your-work-with-issues/creating-an-issue).                                                             |
| `Open in github.dev editor`    | Open the current repository in the github.dev editor. For more information, see [The github.dev web-based editor](/en/codespaces/the-githubdev-web-based-editor#opening-the-web-based-editor).                            |

### File commands

These commands are available only when you open the command palette from a file in a repository.

| Command                     | Behavior                                                                                                                                                                                                                                                                                               |
| :-------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy permalink`            | Create a link to the file that includes the current commit SHA and copy the link to the clipboard. For more information, see [Getting permanent links to files](/en/repositories/working-with-files/using-files/getting-permanent-links-to-files#press-y-to-permalink-to-a-file-in-a-specific-commit). |
| `Open in github.dev editor` | Open the currently displayed file in github.dev editor. For more information, see [The github.dev web-based editor](/en/codespaces/the-githubdev-web-based-editor#opening-the-web-based-editor).                                                                                                       |

### Discussion commands

These commands are available only when you open the command palette from a discussion. They act on your current page and are not affected by the scope set in the command palette.

| Command                   | Behavior                                                                                                                                                                                                                                  |
| :------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Delete discussion...`    | Permanently delete the discussion. For more information, see [Managing discussions](/en/discussions/managing-discussions-for-your-community/managing-discussions#deleting-a-discussion).                                                  |
| `Edit discussion body`    | Open the main body of the discussion ready for editing.                                                                                                                                                                                   |
| `Subscribe`/`unsubscribe` | Opt in or out of notifications for additions to the discussion. For more information, see [About notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/about-notifications). |
| `Transfer discussion...`  | Move the discussion to a different repository. For more information, see [Managing discussions](/en/discussions/managing-discussions-for-your-community/managing-discussions#transferring-a-discussion).                                  |

### Issue commands

These commands are available only when you open the command palette from an issue. They act on your current page and are not affected by the scope set in the command palette.

| Command                          | Behavior                                                                                                                                                                                                                                  |
| :------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Close`/`reopen issue`           | Close or reopen the current issue. For more information, see [About issues](/en/issues/tracking-your-work-with-issues/about-issues).                                                                                                      |
| `Convert issue to discussion...` | Convert the current issue into a discussion. For more information, see [Moderating discussions](/en/discussions/managing-discussions-for-your-community/moderating-discussions#converting-an-issue-to-a-discussion).                      |
| `Delete issue...`                | Delete the current issue. For more information, see [Deleting an issue](/en/issues/tracking-your-work-with-issues/deleting-an-issue).                                                                                                     |
| `Edit issue body`                | Open the main body of the issue ready for editing.                                                                                                                                                                                        |
| `Edit issue title`               | Open the title of the issue ready for editing.                                                                                                                                                                                            |
| `Lock issue`                     | Limit new comments to users with write access to the repository. For more information, see [Locking conversations](/en/communities/moderating-comments-and-conversations/locking-conversations).                                          |
| `Pin`/`unpin issue`              | Change whether or not the issue is shown in the pinned issues section for the repository. For more information, see [Pinning an issue to your repository](/en/issues/tracking-your-work-with-issues/pinning-an-issue-to-your-repository). |
| `Subscribe`/`unsubscribe`        | Opt in or out of notifications for changes to this issue. For more information, see [About notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/about-notifications).       |
| `Transfer issue...`              | Transfer the issue to another repository. For more information, see [Transferring an issue to another repository](/en/issues/tracking-your-work-with-issues/transferring-an-issue-to-another-repository).                                 |

### Pull request commands

These commands are available only when you open the command palette from a pull request. They act on your current page and are not affected by the scope set in the command palette.

| Command                                                    | Behavior                                                                                                                                                                                                                                                                                                                                  |
| :--------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Close`/`reopen pull request`                              | Close or reopen the current pull request. For more information, see [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).                                                                                                                      |
| `Convert to draft`/`Mark pull request as ready for review` | Change the state of the pull request to show it as ready, or not ready, for review. For more information, see [Changing the stage of a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request).                                          |
| `Copy current branch name`                                 | Add the name of the head branch for the pull request to the clipboard.                                                                                                                                                                                                                                                                    |
| `Edit pull request body`                                   | Open the main body of the pull request ready for editing.                                                                                                                                                                                                                                                                                 |
| `Edit pull request title`                                  | Open the title of the pull request ready for editing.                                                                                                                                                                                                                                                                                     |
| `Subscribe`/`unsubscribe`                                  | Opt in or out of notifications for changes to this pull request. For more information, see [About notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/about-notifications).                                                                                                |
| `Update current branch`                                    | Update the head branch of the pull request with changes from the base branch. This is available only for pull requests that target the default branch of the repository. For more information, see [About branches](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches). |# Exploring early access releases with feature preview

You can use feature preview to see products or features that are available in public preview and to enable or disable each feature for your personal account.

## GitHub's release cycle

GitHub's products and features can go through multiple release phases.

| Phase                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Private preview           | The product or feature is under heavy development and often has changing requirements and scope. The feature is available for demonstration and test purposes but may not be documented. Private preview releases are not necessarily feature complete, no service level agreements (SLAs) are provided, and there are no technical support obligations. <br><br> **Note:** A product or feature released as a "Technology Preview" is considered to be in the private preview release stage. Technology Preview releases share the same characteristics of private preview releases as described above. |
| Public preview            | The product or feature is ready for broader distribution. Public preview releases can be public or private, are documented, but do not have any SLAs or technical support obligations.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| General availability (GA) | The product or feature is fully tested and open publicly to all users. GA releases are ready for production use, and associated SLA and technical support obligations apply.                                                                                                                                                                                                                                                                                                                                                                                                                             |

## Exploring public preview releases with feature preview

You can see a list of features that are available in public preview and a brief description for each feature. Each feature includes a link to give feedback.

1. In the upper-right corner of any page, click your profile picture, then click **Feature preview**.
2. To view details for a feature, in the left sidebar, click the feature's name.
3. Optionally, to the right of a feature's name, click **Enable** or **Disable**.# GitHub Terms of Service

<!-- markdownlint-disable search-replace -->

Thank you for using GitHub! We're happy you're here. Please read this Terms of Service agreement carefully before accessing or using GitHub. Because it is such an important contract between us and our users, we have tried to make it as clear as possible. For your convenience, we have presented these terms in a short non-binding summary followed by the full legal terms.

## Summary

| Section                                                                 | What can you find there?                                                                                                                                                                                               |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [A. Definitions](#a-definitions)                                        | Some basic terms, defined in a way that will help you understand this agreement. Refer back up to this section for clarification.                                                                                      |
| [B. Account Terms](#b-account-terms)                                    | These are the basic requirements of having an Account on GitHub.                                                                                                                                                       |
| [C. Acceptable Use](#c-acceptable-use)                                  | These are the basic rules you must follow when using your GitHub Account.                                                                                                                                              |
| [D. User-Generated Content](#d-user-generated-content)                  | You own the content you post on GitHub. However, you have some responsibilities regarding it, and we ask you to grant us some rights so we can provide services to you.                                                |
| [E. Private Repositories](#e-private-repositories)                      | This section talks about how GitHub will treat content you post in private repositories.                                                                                                                               |
| [F. Copyright & DMCA Policy](#f-copyright-infringement-and-dmca-policy) | This section talks about how GitHub will respond if you believe someone is infringing your copyrights on GitHub.                                                                                                       |
| [G. Intellectual Property Notice](#g-intellectual-property-notice)      | This describes GitHub's rights in the website and service.                                                                                                                                                             |
| [H. API Terms](#h-api-terms)                                            | These are the rules for using GitHub's APIs, whether you are using the API for development or data collection.                                                                                                         |
| [I. Additional Product Terms](#i-github-additional-product-terms)       | We have a few specific rules for GitHub's features and products.                                                                                                                                                       |
| [J. Beta Previews](#j-beta-previews)                                    | These are some of the additional terms that apply to GitHub's features that are still in development.                                                                                                                  |
| [K. Payment](#k-payment)                                                | You are responsible for payment. We are responsible for billing you accurately.                                                                                                                                        |
| [L. Cancellation and Termination](#l-cancellation-and-termination)      | You may cancel this agreement and close your Account at any time.                                                                                                                                                      |
| [M. Communications with GitHub](#m-communications-with-github)          | We only use email and other electronic means to stay in touch with our users. We do not provide phone support.                                                                                                         |
| [N. Disclaimer of Warranties](#n-disclaimer-of-warranties)              | We provide our service as is, and we make no promises or guarantees about this service. **Please read this section carefully; you should understand what to expect.**                                                  |
| [O. Limitation of Liability](#o-limitation-of-liability)                | We will not be liable for damages or losses arising from your use or inability to use the service or otherwise arising under this agreement. **Please read this section carefully; it limits our obligations to you.** |
| [P. Release and Indemnification](#p-release-and-indemnification)        | You are fully responsible for your use of the service.                                                                                                                                                                 |
| [Q. Changes to these Terms of Service](#q-changes-to-these-terms)       | We may modify this agreement, but we will give you 30 days' notice of material changes.                                                                                                                                |
| [R. Miscellaneous](#r-miscellaneous)                                    | Please see this section for legal details including our choice of law.                                                                                                                                                 |

## The GitHub Terms of Service

Effective date: November 16, 2020

## A. Definitions

**Short version:** *We use these basic terms throughout the agreement, and they have specific meanings. You should know what we mean when we use each of the terms. There's not going to be a test on it, but it's still useful information.*

1. An "Account" represents your legal relationship with GitHub. A “Personal Account” represents an individual User’s authorization to log in to and use the Service and serves as a User’s identity on GitHub. “Organizations” are shared workspaces that may be associated with a single entity or with one or more Users where multiple Users can collaborate across many projects at once. A Personal Account can be a member of any number of Organizations.
2. The “Agreement” refers, collectively, to all the terms, conditions, notices contained or referenced in this document (the “Terms of Service” or the "Terms") and all other operating rules, policies (including the GitHub Privacy Statement, available at [github.com/site/privacy](https://github.com/site/privacy)) and procedures that we may publish from time to time on the Website. Most of our site policies are available at [docs.github.com/categories/site-policy](/en/site-policy).
3. "Beta Previews" mean software, services, or features identified as alpha, beta, preview, early access, or evaluation, or words or phrases with similar meanings.
4. “Content” refers to content featured or displayed through the Website, including without limitation code, text, data, articles, images, photographs, graphics, software, applications, packages, designs, features, and other materials that are available on the Website or otherwise available through the Service. "Content" also includes Services. “User-Generated Content” is Content, written or otherwise, created or uploaded by our Users. "Your Content" is Content that you create or own.
5. “GitHub,” “We,” and “Us” refer to GitHub, Inc., as well as our affiliates, directors, subsidiaries, contractors, licensors, officers, agents, and employees.
6. The “Service” refers to the applications, software, products, and services provided by GitHub, including any Beta Previews.
7. “The User,” “You,” and “Your” refer to the individual person, company, or organization that has visited or is using the Website or Service; that accesses or uses any part of the Account; or that directs the use of the Account in the performance of its functions. A User must be at least 13 years of age. Special terms may apply for business or government Accounts (See [Section B(5): Additional Terms](#5-additional-terms)).
8. The “Website” refers to GitHub’s website located at [github.com](https://github.com/), and all content, services, and products provided by GitHub at or through the Website. It also refers to GitHub-owned subdomains of github.com, such as [education.github.com](https://education.github.com/) and [pages.github.com](https://pages.github.com/). These Terms also govern GitHub’s conference websites, such as [githubuniverse.com](https://githubuniverse.com/), and product websites, such as [electronjs.org](https://www.electronjs.org/). Occasionally, websites owned by GitHub may provide different or additional terms of service. If those additional terms conflict with this Agreement, the more specific terms apply to the relevant page or service.

## B. Account Terms

**Short version:** *Personal Accounts and Organizations have different administrative controls; a human must create your Account; you must be 13 or over; you must provide a valid email address; and you may not have more than one free Account. You alone are responsible for your Account and anything that happens while you are signed in to or using your Account. You are responsible for keeping your Account secure.*

### 1. Account Controls

* Users. Subject to these Terms, you retain ultimate administrative control over your Personal Account and the Content within it.

* Organizations. The "owner" of an Organization that was created under these Terms has ultimate administrative control over that Organization and the Content within it. Within the Service, an owner can manage User access to the Organization’s data and projects. An Organization may have multiple owners, but there must be at least one Personal Account designated as an owner of an Organization. If you are the owner of an Organization under these Terms, we consider you responsible for the actions that are performed on or through that Organization.

### 2. Required Information

You must provide a valid email address in order to complete the signup process. Any other information requested, such as your real name, is optional, unless you are accepting these terms on behalf of a legal entity (in which case we need more information about the legal entity) or if you opt for a [paid Account](#k-payment), in which case additional information will be necessary for billing purposes.

### 3. Account Requirements

We have a few simple rules for Personal Accounts on GitHub's Service.

* You must be a human to create an Account. Accounts registered by "bots" or other automated methods are not permitted. We do permit machine accounts:
* A machine account is an Account set up by an individual human who accepts the Terms on behalf of the Account, provides a valid email address, and is responsible for its actions. A machine account is used exclusively for performing automated tasks. Multiple users may direct the actions of a machine account, but the owner of the Account is ultimately responsible for the machine's actions. You may maintain no more than one free machine account in addition to your free Personal Account.
* One person or legal entity may maintain no more than one free Account (if you choose to control a machine account as well, that's fine, but it can only be used for running a machine).
* You must be age 13 or older. While we are thrilled to see brilliant young coders get excited by learning to program, we must comply with United States law. GitHub does not target our Service to children under 13, and we do not permit any Users under 13 on our Service. If we learn of any User under the age of 13, we will [terminate that User’s Account immediately](#l-cancellation-and-termination). If you are a resident of a country outside the United States, your country’s minimum age may be older; in such a case, you are responsible for complying with your country’s laws.
* Your login may only be used by one person — i.e., a single login may not be shared by multiple people. A paid Organization may only provide access to as many Personal Accounts as your subscription allows.
* You may not use GitHub in violation of export control or sanctions laws of the United States or any other applicable jurisdiction. You may not use GitHub if you are or are working on behalf of a [Specially Designated National (SDN)](https://www.treasury.gov/resource-center/sanctions/SDN-List/Pages/default.aspx) or a person subject to similar blocking or denied party prohibitions administered by a U.S. government agency. GitHub may allow persons in certain sanctioned countries or territories to access certain GitHub services pursuant to U.S. government authorizations. For more information, please see our [Export Controls policy](/en/site-policy/other-site-policies/github-and-trade-controls).

### 4. Account Security

You are responsible for keeping your Account secure while you use our Service. We offer tools such as two-factor authentication to help you maintain your Account's security, but the content of your Account and its security are up to you.

* You are responsible for all content posted and activity that occurs under your Account (even when content is posted by others who have Accounts under your Account).
* You are responsible for maintaining the security of your Account and password. GitHub cannot and will not be liable for any loss or damage from your failure to comply with this security obligation.
* You will promptly notify GitHub by contacting us through the [GitHub Support portal](https://support.github.com/) if you become aware of any unauthorized use of, or access to, our Service through your Account, including any unauthorized use of your password or Account.

### 5. Additional Terms

In some situations, third parties' terms may apply to your use of GitHub. For example, you may be a member of an organization on GitHub with its own terms or license agreements; you may download an application that integrates with GitHub; or you may use GitHub to authenticate to another service. Please be aware that while these Terms are our full agreement with you, other parties' terms govern their relationships with you.

If you are a government User or otherwise accessing or using any GitHub Service in a government capacity, this [Government Amendment to GitHub Terms of Service](/en/site-policy/site-policy-deprecated/amendment-to-github-terms-of-service-applicable-to-us-federal-government-users) applies to you, and you agree to its provisions.

If you have signed up for GitHub Enterprise Cloud, the [Enterprise Cloud Addendum](/en/site-policy/site-policy-deprecated/github-enterprise-service-level-agreement) applies to you, and you agree to its provisions.

## C. Acceptable Use

**Short version:** *GitHub hosts a wide variety of collaborative projects from all over the world, and that collaboration only works when our users are able to work together in good faith. While using the service, you must follow the terms of this section, which include some restrictions on content you can post, conduct on the service, and other limitations. In short, be excellent to each other.*

Your use of the Website and Service must not violate any applicable laws, including copyright or trademark laws, export control or sanctions laws, or other laws in your jurisdiction. You are responsible for making sure that your use of the Service is in compliance with laws and any applicable regulations.

You agree that you will not under any circumstances violate our [Acceptable Use Policies](/en/site-policy/acceptable-use-policies/github-acceptable-use-policies) or [Community Guidelines](/en/site-policy/github-terms/github-community-guidelines).

## D. User-Generated Content

**Short version:** *You own content you create, but you allow us certain rights to it, so that we can display and share the content you post. You still have control over your content, and responsibility for it, and the rights you grant us are limited to those we need to provide the service. We have the right to remove content or close Accounts if we need to.*

### 1. Responsibility for User-Generated Content

You may create or upload User-Generated Content while using the Service. You are solely responsible for the content of, and for any harm resulting from, any User-Generated Content that you post, upload, link to or otherwise make available via the Service, regardless of the form of that Content. We are not responsible for any public display or misuse of your User-Generated Content.

### 2. GitHub May Remove Content

We have the right to refuse or remove any User-Generated Content that, in our sole discretion, violates any laws or [GitHub terms or policies](/en/site-policy). User-Generated Content displayed on GitHub Mobile may be subject to mobile app stores' additional terms.

### 3. Ownership of Content, Right to Post, and License Grants

You retain ownership of and responsibility for Your Content. If you're posting anything you did not create yourself or do not own the rights to, you agree that you are responsible for any Content you post; that you will only submit Content that you have the right to post; and that you will fully comply with any third party licenses relating to Content you post.

Because you retain ownership of and responsibility for Your Content, we need you to grant us — and other GitHub Users — certain legal permissions, listed in Sections D.4 — D.7. These license grants apply to Your Content. If you upload Content that already comes with a license granting GitHub the permissions we need to run our Service, no additional license is required. You understand that you will not receive any payment for any of the rights granted in Sections D.4 — D.7. The licenses you grant to us will end when you remove Your Content from our servers, unless other Users have forked it.

### 4. License Grant to Us

We need the legal right to do things like host Your Content, publish it, and share it. You grant us and our legal successors the right to store, archive, parse, and display Your Content, and make incidental copies, as necessary to provide the Service, including improving the Service over time. This license includes the right to do things like copy it to our database and make backups; show it to you and other users; parse it into a search index or otherwise analyze it on our servers; share it with other users; and perform it, in case Your Content is something like music or video.

This license does not grant GitHub the right to sell Your Content. It also does not grant GitHub the right to otherwise distribute or use Your Content outside of our provision of the Service, except that as part of the right to archive Your Content, GitHub may permit our partners to store and archive Your Content in public repositories in connection with the [GitHub Arctic Code Vault and GitHub Archive Program](https://archiveprogram.github.com/).

### 5. License Grant to Other Users

Any User-Generated Content you post publicly, including issues, comments, and contributions to other Users' repositories, may be viewed by others. By setting your repositories to be viewed publicly, you agree to allow others to view and "fork" your repositories (this means that others may make their own copies of Content from your repositories in repositories they control).

If you set your pages and repositories to be viewed publicly, you grant each User of GitHub a nonexclusive, worldwide license to use, display, and perform Your Content through the GitHub Service and to reproduce Your Content solely on GitHub as permitted through GitHub's functionality (for example, through forking). You may grant further rights if you [adopt a license](/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-license-to-a-repository#including-an-open-source-license-in-your-repository). If you are uploading Content you did not create or own, you are responsible for ensuring that the Content you upload is licensed under terms that grant these permissions to other GitHub Users.

### 6. Contributions Under Repository License

Whenever you add Content to a repository containing notice of a license, you license that Content under the same terms, and you agree that you have the right to license that Content under those terms. If you have a separate agreement to license that Content under different terms, such as a contributor license agreement, that agreement will supersede.

Isn't this just how it works already? Yep. This is widely accepted as the norm in the open-source community; it's commonly referred to by the shorthand "inbound=outbound". We're just making it explicit.

### 7. Moral Rights

You retain all moral rights to Your Content that you upload, publish, or submit to any part of the Service, including the rights of integrity and attribution. However, you waive these rights and agree not to assert them against us, to enable us to reasonably exercise the rights granted in Section D.4, but not otherwise.

To the extent this agreement is not enforceable by applicable law, you grant GitHub the rights we need to use Your Content without attribution and to make reasonable adaptations of Your Content as necessary to render the Website and provide the Service.

### 8. Access Reciprocity

By using automated means to access, collect, or otherwise use (“Access”) any publicly accessible Content from the Service for the purpose of developing or training any commercially available artificial intelligence model, machine learning system, or similar technology (a "Commercial AI System"), you hereby waive any and all policies, terms, conditions, or contractual provisions governing products, services, websites or datasets you own or operate that would otherwise prohibit, restrict, or place conditions upon GitHub's Access to any publicly accessible data, information or content associated with your products or services, including for the purpose of developing or training any Commercial AI System. You further agree not to impose technical or other targeted measures to restrict or retaliate against such Access.

This Section D.8 does not apply to Access solely for the purpose of academic research or if, on the date you Access the Content, the number of monthly active users of the products or services made available by you is less than 700 million in the preceding calendar month. For the purposes of this Section, "you" shall refer to you and any entity that directly or indirectly controls, is controlled by, or is under common control with you (affiliates).

## E. Private Repositories

**Short version:** *We treat the content of private repositories as confidential, and we only access it as described in our Privacy Statement—for security purposes, to assist the repository owner with a support matter, to maintain the integrity of the Service, to comply with our legal obligations, if we have reason to believe the contents are in violation of the law, or with your consent.*

### 1. Control of Private Repositories

Some Accounts may have private repositories, which allow the User to control access to Content.

### 2. Confidentiality of Private Repositories

GitHub considers the contents of private repositories to be confidential to you. GitHub will protect the contents of private repositories from unauthorized use, access, or disclosure in the same manner that we would use to protect our own confidential information of a similar nature and in no event with less than a reasonable degree of care.

### 3. Access

GitHub personnel may only access the content of your private repositories in the situations described in our [Privacy Statement](/en/site-policy/privacy-policies/github-privacy-statement#repository-contents).

You may choose to enable additional access to your private repositories. For example:

* You may enable various GitHub services or features that require additional rights to Your Content in private repositories. These rights may vary depending on the service or feature, but GitHub will continue to treat your private repository Content as confidential. If those services or features require rights in addition to those we need to provide the GitHub Service, we will provide an explanation of those rights.

Additionally, we may be [compelled by law](/en/site-policy/privacy-policies/github-privacy-statement#for-legal-disclosure) to disclose the contents of your private repositories.

GitHub will provide notice regarding our access to private repository content, unless [for legal disclosure](/en/site-policy/privacy-policies/github-privacy-statement#for-legal-disclosure), to comply with our legal obligations, or where otherwise bound by requirements under law, for automated scanning, or if in response to a security threat or other risk to security.

## F. Copyright Infringement and DMCA Policy

If you believe that content on our website violates your copyright, please contact us in accordance with our [Digital Millennium Copyright Act Policy](/en/site-policy/content-removal-policies/dmca-takedown-policy). If you are a copyright owner and you believe that content on GitHub violates your rights, please contact us via [our convenient DMCA form](https://github.com/contact/dmca) or by emailing <copyright@github.com>. There may be legal consequences for sending a false or frivolous takedown notice. Before sending a takedown request, you must consider legal uses such as fair use and licensed uses.

We will terminate the Accounts of [repeat infringers](/en/site-policy/content-removal-policies/dmca-takedown-policy#e-repeated-infringement) of this policy.

## G. Intellectual Property Notice

**Short version:** *We own the service and all of our content. In order for you to use our content, we give you certain rights to it, but you may only use our content in the way we have allowed.*

### 1. GitHub's Rights to Content

GitHub and our licensors, vendors, agents, and/or our content providers retain ownership of all intellectual property rights of any kind related to the Website and Service. We reserve all rights that are not expressly granted to you under this Agreement or by law. The look and feel of the Website and Service is copyright © GitHub, Inc. All rights reserved. You may not duplicate, copy, or reuse any portion of the HTML/CSS, JavaScript, or visual design elements or concepts without express written permission from GitHub.

### 2. GitHub Trademarks and Logos

If you’d like to use GitHub’s trademarks, you must follow all of our trademark guidelines, including those on our logos page: <https://github.com/logos>.

### 3. License to GitHub Policies

This Agreement is licensed under this [Creative Commons Zero license](https://creativecommons.org/publicdomain/zero/1.0/). For details, see our [site-policy repository](https://github.com/github/site-policy#license).

## H. API Terms

**Short version:** *You agree to these Terms of Service, plus this Section H, when using any of GitHub's APIs (Application Provider Interface), including use of the API through a third party product that accesses GitHub.*

Abuse or excessively frequent requests to GitHub via the API may result in the temporary or permanent suspension of your Account's access to the API. GitHub, in our sole discretion, will determine abuse or excessive usage of the API. We will make a reasonable attempt to warn you via email prior to suspension.

You may not share API tokens to exceed GitHub's rate limitations.

You may not use the API to download data or Content from GitHub for spamming purposes, including for the purposes of selling GitHub users' personal information, such as to recruiters, headhunters, and job boards.

All use of the GitHub API is subject to these Terms of Service and the [GitHub Privacy Statement](https://github.com/site/privacy).

GitHub may offer subscription-based access to our API for those Users who require high-throughput access or access that would result in resale of GitHub's Service.

## I. GitHub Additional Product Terms

**Short version:** *You need to follow certain specific terms and conditions for GitHub's various features and products, and you agree to the Supplemental Terms and Conditions when you agree to this Agreement.*

Some Service features may be subject to additional terms specific to that feature or product as set forth in the GitHub Additional Product Terms. By accessing or using the Services, you also agree to the [GitHub Additional Product Terms](/en/site-policy/github-terms/github-terms-for-additional-products-and-features).

## J. Beta Previews

**Short version:** *Beta Previews may not be supported or may change at any time. You may receive confidential information through those programs that must remain confidential while the program is private. We'd love your feedback to make our Beta Previews better.*

### 1. Subject to Change

Beta Previews may not be supported and may be changed at any time without notice. In addition, Beta Previews are not subject to the same security measures and auditing to which the Service has been and is subject. **By using a Beta Preview, you use it at your own risk.**

### 2. Confidentiality

As a user of Beta Previews, you may get access to special information that isn’t available to the rest of the world. Due to the sensitive nature of this information, it’s important for us to make sure that you keep that information secret.

**Confidentiality Obligations.** You agree that any non-public Beta Preview information we give you, such as information about a private Beta Preview, will be considered GitHub’s confidential information (collectively, “Confidential Information”), regardless of whether it is marked or identified as such. You agree to only use such Confidential Information for the express purpose of testing and evaluating the Beta Preview (the “Purpose”), and not for any other purpose. You should use the same degree of care as you would with your own confidential information, but no less than reasonable precautions to prevent any unauthorized use, disclosure, publication, or dissemination of our Confidential Information. You promise not to disclose, publish, or disseminate any Confidential Information to any third party, unless we don’t otherwise prohibit or restrict such disclosure (for example, you might be part of a GitHub-organized group discussion about a private Beta Preview feature).

**Exceptions.** Confidential Information will not include information that is: (a) or becomes publicly available without breach of this Agreement through no act or inaction on your part (such as when a private Beta Preview becomes a public Beta Preview); (b) known to you before we disclose it to you; (c) independently developed by you without breach of any confidentiality obligation to us or any third party; or (d) disclosed with permission from GitHub. You will not violate the terms of this Agreement if you are required to disclose Confidential Information pursuant to operation of law, provided GitHub has been given reasonable advance written notice to object, unless prohibited by law.

### 3. Feedback

We’re always trying to improve of products and services, and your feedback as a Beta Preview user will help us do that. If you choose to give us any ideas, know-how, algorithms, code contributions, suggestions, enhancement requests, recommendations or any other feedback for our products or services (collectively, “Feedback”), you acknowledge and agree that GitHub will have a royalty-free, fully paid-up, worldwide, transferable, sub-licensable, irrevocable and perpetual license to implement, use, modify, commercially exploit and/or incorporate the Feedback into our products, services, and documentation.

## K. Payment

**Short version:** *You are responsible for any fees associated with your use of GitHub. We are responsible for communicating those fees to you clearly and accurately, and letting you know well in advance if those prices change.*

### 1. Pricing

Our pricing and payment terms are available at [github.com/pricing](https://github.com/pricing). If you agree to a subscription price, that will remain your price for the duration of the payment term; however, prices are subject to change at the end of a payment term.

### 2. Upgrades, Downgrades, and Changes

* We will immediately bill you when you upgrade from the free plan to any paying plan.
* If you change from a monthly billing plan to a yearly billing plan, GitHub will bill you for a full year at the next monthly billing date.
* If you upgrade to a higher level of service, we will bill you for the upgraded plan immediately.
* You may change your level of service at any time by [choosing a plan option](https://github.com/pricing) or going into your [Billing settings](https://github.com/settings/billing). If you choose to downgrade your Account, you may lose access to Content, features, or capacity of your Account. Please see our section on [Cancellation](#l-cancellation-and-termination) for information on getting a copy of that Content.

### 3. Billing Schedule; No Refunds

**Payment Based on Plan** For monthly or yearly payment plans, the Service is billed in advance on a monthly or yearly basis respectively and is non-refundable. There will be no refunds or credits for partial months of service, downgrade refunds, or refunds for months unused with an open Account; however, the service will remain active for the length of the paid billing period. In order to treat everyone equally, no exceptions will be made.

**Payment Based on Usage** Some Service features are billed based on your usage. A limited quantity of these Service features may be included in your plan for a limited term without additional charge. If you choose to use paid Service features beyond the quantity included in your plan, you pay for those Service features based on your actual usage in the preceding month. Monthly payment for these purchases will be charged on a periodic basis in arrears. See [GitHub Additional Product Terms for Details](/en/site-policy/github-terms/github-terms-for-additional-products-and-features).

**Invoicing** For invoiced Users, User agrees to pay the fees in full, up front without deduction or setoff of any kind, in U.S. Dollars. User must pay the fees within thirty (30) days of the GitHub invoice date. Amounts payable under this Agreement are non-refundable, except as otherwise provided in this Agreement. If User fails to pay any fees on time, GitHub reserves the right, in addition to taking any other action at law or equity, to (i) charge interest on past due amounts at 1.0% per month or the highest interest rate allowed by law, whichever is less, and to charge all expenses of recovery, and (ii) terminate the applicable order form. User is solely responsible for all taxes, fees, duties and governmental assessments (except for taxes based on GitHub's net income) that are imposed or become due in connection with this Agreement.

### 4. Authorization

By agreeing to these Terms, you are giving us permission to charge your on-file credit card, PayPal account, or other approved methods of payment for fees that you authorize for GitHub.

### 5. Responsibility for Payment

You are responsible for all fees, including taxes, associated with your use of the Service. By using the Service, you agree to pay GitHub any charge incurred in connection with your use of the Service. If you dispute the matter, contact us through the [GitHub Support portal](https://support.github.com/). You are responsible for providing us with a valid means of payment for paid Accounts. Free Accounts are not required to provide payment information.

## L. Cancellation and Termination

**Short version:** *You may close your Account at any time. If you do, we'll treat your information responsibly.*

### 1. Account Cancellation

It is your responsibility to properly cancel your Account with GitHub. You can [cancel your Account at any time](/en/billing/managing-the-plan-for-your-github-account/downgrading-your-accounts-plan) by going into your Settings in the global navigation bar at the top of the screen. The Account screen provides a simple, no questions asked cancellation link. We are not able to cancel Accounts in response to an email or phone request.

### 2. Upon Cancellation

We will retain and use your information as necessary to comply with our legal obligations, resolve disputes, and enforce our agreements, but barring legal requirements, we will delete your full profile and the Content of your repositories within 90 days of cancellation or termination (though some information may remain in encrypted backups). This information cannot be recovered once your Account is canceled.

We will not delete Content that you have contributed to other Users' repositories or that other Users have forked.

Upon request, we will make a reasonable effort to provide an Account owner with a copy of your lawful, non-infringing Account contents after Account cancellation, termination, or downgrade. You must make this request within 90 days of cancellation, termination, or downgrade.

### 3. GitHub May Terminate

GitHub has the right to suspend or terminate your access to all or any part of the Website at any time, with or without cause, with or without notice, effective immediately. GitHub reserves the right to refuse service to anyone for any reason at any time.

### 4. Survival

All provisions of this Agreement which, by their nature, should survive termination *will* survive termination — including, without limitation: ownership provisions, warranty disclaimers, indemnity, and limitations of liability.

## M. Communications with GitHub

**Short version:** *We use email and other electronic means to stay in touch with our users.*

### 1. Electronic Communication Required

For contractual purposes, you (1) consent to receive communications from us in an electronic form via the email address you have submitted or via the Service; and (2) agree that all Terms of Service, agreements, notices, disclosures, and other communications that we provide to you electronically satisfy any legal requirement that those communications would satisfy if they were on paper. This section does not affect your non-waivable rights.

### 2. Legal Notice to GitHub Must Be in Writing

Communications made through email or GitHub Support's messaging system will not constitute legal notice to GitHub or any of its officers, employees, agents or representatives in any situation where notice to GitHub is required by contract or any law or regulation. Legal notice to GitHub must be in writing and [served on GitHub's legal agent](/en/site-policy/other-site-policies/guidelines-for-legal-requests-of-user-data#submitting-requests).

### 3. No Phone Support

GitHub only offers support via email, in-Service communications, and electronic messages. We do not offer telephone support.

## N. Disclaimer of Warranties

**Short version:** *We provide our service as is, and we make no promises or guarantees about this service. Please read this section carefully; you should understand what to expect.*

GitHub provides the Website and the Service “as is” and “as available,” without warranty of any kind. Without limiting this, we expressly disclaim all warranties, whether express, implied or statutory, regarding the Website and the Service including without limitation any warranty of merchantability, fitness for a particular purpose, title, security, accuracy and non-infringement.

GitHub does not warrant that the Service will meet your requirements; that the Service will be uninterrupted, timely, secure, or error-free; that the information provided through the Service is accurate, reliable or correct; that any defects or errors will be corrected; that the Service will be available at any particular time or location; or that the Service is free of viruses or other harmful components. You assume full responsibility and risk of loss resulting from your downloading and/or use of files, information, content or other material obtained from the Service.

## O. Limitation of Liability

**Short version:** *We will not be liable for damages or losses arising from your use or inability to use the service or otherwise arising under this agreement. Please read this section carefully; it limits our obligations to you.*

You understand and agree that we will not be liable to you or any third party for any loss of profits, use, goodwill, or data, or for any incidental, indirect, special, consequential or exemplary damages, however arising, that result from

<!-- markdownlint-disable GHD034 -->

* the use, disclosure, or display of your User-Generated Content;
* your use or inability to use the Service;
* any modification, price change, suspension or discontinuance of the Service;
* the Service generally or the software or systems that make the Service available;
* unauthorized access to or alterations of your transmissions or data;
* statements or conduct of any third party on the Service;
* any other user interactions that you input or receive through your use of the Service; or
* any other matter relating to the Service.

<!-- markdownlint-enable GHD034 -->

Our liability is limited whether or not we have been informed of the possibility of such damages, and even if a remedy set forth in this Agreement is found to have failed of its essential purpose. We will have no liability for any failure or delay due to matters beyond our reasonable control.

## P. Release and Indemnification

**Short version:** *You are responsible for your use of the service. If you harm someone else or get into a dispute with someone else, we will not be involved.*

If you have a dispute with one or more Users, you agree to release GitHub from any and all claims, demands and damages (actual and consequential) of every kind and nature, known and unknown, arising out of or in any way connected with such disputes.

You agree to indemnify us, defend us, and hold us harmless from and against any and all claims, liabilities, and expenses, including attorneys’ fees, arising out of your use of the Website and the Service, including but not limited to your violation of this Agreement, provided that GitHub (1) promptly gives you written notice of the claim, demand, suit or proceeding; (2) gives you sole control of the defense and settlement of the claim, demand, suit or proceeding (provided that you may not settle any claim, demand, suit or proceeding unless the settlement unconditionally releases GitHub of all liability); and (3) provides to you all reasonable assistance, at your expense.

## Q. Changes to These Terms

**Short version:** *We want our users to be informed of important changes to our terms, but some changes aren't that important — we don't want to bother you every time we fix a typo. So while we may modify this agreement at any time, we will notify users of any material changes and give you time to adjust to them.*

We reserve the right, at our sole discretion, to amend these Terms of Service at any time and will update these Terms of Service in the event of any such amendments. We will notify our Users of material changes to this Agreement, such as price increases, at least 30 days prior to the change taking effect by posting a notice on our Website or sending email to the primary email address specified in your GitHub account. Customer's continued use of the Service after those 30 days constitutes agreement to those revisions of this Agreement. For any other modifications, your continued use of the Website constitutes agreement to our revisions of these Terms of Service. You can view all changes to these Terms in our [Site Policy](https://github.com/github/site-policy) repository.

We reserve the right at any time and from time to time to modify or discontinue, temporarily or permanently, the Website (or any part of it) with or without notice.

## R. Miscellaneous

### 1. Governing Law

Except to the extent applicable law provides otherwise, this Agreement between you and GitHub and any access to or use of the Website or the Service are governed by the federal laws of the United States of America and the laws of the State of California, without regard to conflict of law provisions. You and GitHub agree to submit to the exclusive jurisdiction and venue of the courts located in the City and County of San Francisco, California. However, any claim for injunctive relief with respect to a violation of section D.8 may be brought in any jurisdiction.

### 2. Non-Assignability

GitHub may assign or delegate these Terms of Service and/or the [GitHub Privacy Statement](https://github.com/site/privacy), in whole or in part, to any person or entity at any time with or without your consent, including the license grant in Section D.4. You may not assign or delegate any rights or obligations under the Terms of Service or Privacy Statement without our prior written consent, and any unauthorized assignment and delegation by you is void.

### 3. Section Headings and Summaries

Throughout this Agreement, each section includes titles and brief summaries of the following terms and conditions. These section titles and brief summaries are not legally binding.

### 4. Severability, No Waiver, and Survival

If any part of this Agreement is held invalid or unenforceable, that portion of the Agreement will be construed to reflect the parties’ original intent. The remaining portions will remain in full force and effect. Any failure on the part of GitHub to enforce any provision of this Agreement will not be considered a waiver of our right to enforce such provision. Our rights under this Agreement will survive any termination of this Agreement.

### 5. Amendments; Complete Agreement

This Agreement may only be modified by a written amendment signed by an authorized representative of GitHub, or by the posting by GitHub of a revised version in accordance with [Section Q. Changes to These Terms](#q-changes-to-these-terms). These Terms of Service, together with the GitHub Privacy Statement, represent the complete and exclusive statement of the agreement between you and us. This Agreement supersedes any proposal or prior agreement oral or written, and any other communications between you and GitHub relating to the subject matter of these terms including any confidentiality or nondisclosure agreements.

### 6. Questions

Questions about the Terms of Service? Contact us through the [GitHub Support portal](https://support.github.com/).# GitHub Terms of Service

<!-- markdownlint-disable search-replace -->

Thank you for using GitHub! We're happy you're here. Please read this Terms of Service agreement carefully before accessing or using GitHub. Because it is such an important contract between us and our users, we have tried to make it as clear as possible. For your convenience, we have presented these terms in a short non-binding summary followed by the full legal terms.

## Summary

| Section                                                                 | What can you find there?                                                                                                                                                                                               |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [A. Definitions](#a-definitions)                                        | Some basic terms, defined in a way that will help you understand this agreement. Refer back up to this section for clarification.                                                                                      |
| [B. Account Terms](#b-account-terms)                                    | These are the basic requirements of having an Account on GitHub.                                                                                                                                                       |
| [C. Acceptable Use](#c-acceptable-use)                                  | These are the basic rules you must follow when using your GitHub Account.                                                                                                                                              |
| [D. User-Generated Content](#d-user-generated-content)                  | You own the content you post on GitHub. However, you have some responsibilities regarding it, and we ask you to grant us some rights so we can provide services to you.                                                |
| [E. Private Repositories](#e-private-repositories)                      | This section talks about how GitHub will treat content you post in private repositories.                                                                                                                               |
| [F. Copyright & DMCA Policy](#f-copyright-infringement-and-dmca-policy) | This section talks about how GitHub will respond if you believe someone is infringing your copyrights on GitHub.                                                                                                       |
| [G. Intellectual Property Notice](#g-intellectual-property-notice)      | This describes GitHub's rights in the website and service.                                                                                                                                                             |
| [H. API Terms](#h-api-terms)                                            | These are the rules for using GitHub's APIs, whether you are using the API for development or data collection.                                                                                                         |
| [I. Additional Product Terms](#i-github-additional-product-terms)       | We have a few specific rules for GitHub's features and products.                                                                                                                                                       |
| [J. Beta Previews](#j-beta-previews)                                    | These are some of the additional terms that apply to GitHub's features that are still in development.                                                                                                                  |
| [K. Payment](#k-payment)                                                | You are responsible for payment. We are responsible for billing you accurately.                                                                                                                                        |
| [L. Cancellation and Termination](#l-cancellation-and-termination)      | You may cancel this agreement and close your Account at any time.                                                                                                                                                      |
| [M. Communications with GitHub](#m-communications-with-github)          | We only use email and other electronic means to stay in touch with our users. We do not provide phone support.                                                                                                         |
| [N. Disclaimer of Warranties](#n-disclaimer-of-warranties)              | We provide our service as is, and we make no promises or guarantees about this service. **Please read this section carefully; you should understand what to expect.**                                                  |
| [O. Limitation of Liability](#o-limitation-of-liability)                | We will not be liable for damages or losses arising from your use or inability to use the service or otherwise arising under this agreement. **Please read this section carefully; it limits our obligations to you.** |
| [P. Release and Indemnification](#p-release-and-indemnification)        | You are fully responsible for your use of the service.                                                                                                                                                                 |
| [Q. Changes to these Terms of Service](#q-changes-to-these-terms)       | We may modify this agreement, but we will give you 30 days' notice of material changes.                                                                                                                                |
| [R. Miscellaneous](#r-miscellaneous)                                    | Please see this section for legal details including our choice of law.                                                                                                                                                 |

## The GitHub Terms of Service

Effective date: November 16, 2020

## A. Definitions

**Short version:** *We use these basic terms throughout the agreement, and they have specific meanings. You should know what we mean when we use each of the terms. There's not going to be a test on it, but it's still useful information.*

1. An "Account" represents your legal relationship with GitHub. A “Personal Account” represents an individual User’s authorization to log in to and use the Service and serves as a User’s identity on GitHub. “Organizations” are shared workspaces that may be associated with a single entity or with one or more Users where multiple Users can collaborate across many projects at once. A Personal Account can be a member of any number of Organizations.
2. The “Agreement” refers, collectively, to all the terms, conditions, notices contained or referenced in this document (the “Terms of Service” or the "Terms") and all other operating rules, policies (including the GitHub Privacy Statement, available at [github.com/site/privacy](https://github.com/site/privacy)) and procedures that we may publish from time to time on the Website. Most of our site policies are available at [docs.github.com/categories/site-policy](/en/site-policy).
3. "Beta Previews" mean software, services, or features identified as alpha, beta, preview, early access, or evaluation, or words or phrases with similar meanings.
4. “Content” refers to content featured or displayed through the Website, including without limitation code, text, data, articles, images, photographs, graphics, software, applications, packages, designs, features, and other materials that are available on the Website or otherwise available through the Service. "Content" also includes Services. “User-Generated Content” is Content, written or otherwise, created or uploaded by our Users. "Your Content" is Content that you create or own.
5. “GitHub,” “We,” and “Us” refer to GitHub, Inc., as well as our affiliates, directors, subsidiaries, contractors, licensors, officers, agents, and employees.
6. The “Service” refers to the applications, software, products, and services provided by GitHub, including any Beta Previews.
7. “The User,” “You,” and “Your” refer to the individual person, company, or organization that has visited or is using the Website or Service; that accesses or uses any part of the Account; or that directs the use of the Account in the performance of its functions. A User must be at least 13 years of age. Special terms may apply for business or government Accounts (See [Section B(5): Additional Terms](#5-additional-terms)).
8. The “Website” refers to GitHub’s website located at [github.com](https://github.com/), and all content, services, and products provided by GitHub at or through the Website. It also refers to GitHub-owned subdomains of github.com, such as [education.github.com](https://education.github.com/) and [pages.github.com](https://pages.github.com/). These Terms also govern GitHub’s conference websites, such as [githubuniverse.com](https://githubuniverse.com/), and product websites, such as [electronjs.org](https://www.electronjs.org/). Occasionally, websites owned by GitHub may provide different or additional terms of service. If those additional terms conflict with this Agreement, the more specific terms apply to the relevant page or service.

## B. Account Terms

**Short version:** *Personal Accounts and Organizations have different administrative controls; a human must create your Account; you must be 13 or over; you must provide a valid email address; and you may not have more than one free Account. You alone are responsible for your Account and anything that happens while you are signed in to or using your Account. You are responsible for keeping your Account secure.*

### 1. Account Controls

* Users. Subject to these Terms, you retain ultimate administrative control over your Personal Account and the Content within it.

* Organizations. The "owner" of an Organization that was created under these Terms has ultimate administrative control over that Organization and the Content within it. Within the Service, an owner can manage User access to the Organization’s data and projects. An Organization may have multiple owners, but there must be at least one Personal Account designated as an owner of an Organization. If you are the owner of an Organization under these Terms, we consider you responsible for the actions that are performed on or through that Organization.

### 2. Required Information

You must provide a valid email address in order to complete the signup process. Any other information requested, such as your real name, is optional, unless you are accepting these terms on behalf of a legal entity (in which case we need more information about the legal entity) or if you opt for a [paid Account](#k-payment), in which case additional information will be necessary for billing purposes.

### 3. Account Requirements

We have a few simple rules for Personal Accounts on GitHub's Service.

* You must be a human to create an Account. Accounts registered by "bots" or other automated methods are not permitted. We do permit machine accounts:
* A machine account is an Account set up by an individual human who accepts the Terms on behalf of the Account, provides a valid email address, and is responsible for its actions. A machine account is used exclusively for performing automated tasks. Multiple users may direct the actions of a machine account, but the owner of the Account is ultimately responsible for the machine's actions. You may maintain no more than one free machine account in addition to your free Personal Account.
* One person or legal entity may maintain no more than one free Account (if you choose to control a machine account as well, that's fine, but it can only be used for running a machine).
* You must be age 13 or older. While we are thrilled to see brilliant young coders get excited by learning to program, we must comply with United States law. GitHub does not target our Service to children under 13, and we do not permit any Users under 13 on our Service. If we learn of any User under the age of 13, we will [terminate that User’s Account immediately](#l-cancellation-and-termination). If you are a resident of a country outside the United States, your country’s minimum age may be older; in such a case, you are responsible for complying with your country’s laws.
* Your login may only be used by one person — i.e., a single login may not be shared by multiple people. A paid Organization may only provide access to as many Personal Accounts as your subscription allows.
* You may not use GitHub in violation of export control or sanctions laws of the United States or any other applicable jurisdiction. You may not use GitHub if you are or are working on behalf of a [Specially Designated National (SDN)](https://www.treasury.gov/resource-center/sanctions/SDN-List/Pages/default.aspx) or a person subject to similar blocking or denied party prohibitions administered by a U.S. government agency. GitHub may allow persons in certain sanctioned countries or territories to access certain GitHub services pursuant to U.S. government authorizations. For more information, please see our [Export Controls policy](/en/site-policy/other-site-policies/github-and-trade-controls).

### 4. Account Security

You are responsible for keeping your Account secure while you use our Service. We offer tools such as two-factor authentication to help you maintain your Account's security, but the content of your Account and its security are up to you.

* You are responsible for all content posted and activity that occurs under your Account (even when content is posted by others who have Accounts under your Account).
* You are responsible for maintaining the security of your Account and password. GitHub cannot and will not be liable for any loss or damage from your failure to comply with this security obligation.
* You will promptly notify GitHub by contacting us through the [GitHub Support portal](https://support.github.com/) if you become aware of any unauthorized use of, or access to, our Service through your Account, including any unauthorized use of your password or Account.

### 5. Additional Terms

In some situations, third parties' terms may apply to your use of GitHub. For example, you may be a member of an organization on GitHub with its own terms or license agreements; you may download an application that integrates with GitHub; or you may use GitHub to authenticate to another service. Please be aware that while these Terms are our full agreement with you, other parties' terms govern their relationships with you.

If you are a government User or otherwise accessing or using any GitHub Service in a government capacity, this [Government Amendment to GitHub Terms of Service](/en/site-policy/site-policy-deprecated/amendment-to-github-terms-of-service-applicable-to-us-federal-government-users) applies to you, and you agree to its provisions.

If you have signed up for GitHub Enterprise Cloud, the [Enterprise Cloud Addendum](/en/site-policy/site-policy-deprecated/github-enterprise-service-level-agreement) applies to you, and you agree to its provisions.

## C. Acceptable Use

**Short version:** *GitHub hosts a wide variety of collaborative projects from all over the world, and that collaboration only works when our users are able to work together in good faith. While using the service, you must follow the terms of this section, which include some restrictions on content you can post, conduct on the service, and other limitations. In short, be excellent to each other.*

Your use of the Website and Service must not violate any applicable laws, including copyright or trademark laws, export control or sanctions laws, or other laws in your jurisdiction. You are responsible for making sure that your use of the Service is in compliance with laws and any applicable regulations.

You agree that you will not under any circumstances violate our [Acceptable Use Policies](/en/site-policy/acceptable-use-policies/github-acceptable-use-policies) or [Community Guidelines](/en/site-policy/github-terms/github-community-guidelines).

## D. User-Generated Content

**Short version:** *You own content you create, but you allow us certain rights to it, so that we can display and share the content you post. You still have control over your content, and responsibility for it, and the rights you grant us are limited to those we need to provide the service. We have the right to remove content or close Accounts if we need to.*

### 1. Responsibility for User-Generated Content

You may create or upload User-Generated Content while using the Service. You are solely responsible for the content of, and for any harm resulting from, any User-Generated Content that you post, upload, link to or otherwise make available via the Service, regardless of the form of that Content. We are not responsible for any public display or misuse of your User-Generated Content.

### 2. GitHub May Remove Content

We have the right to refuse or remove any User-Generated Content that, in our sole discretion, violates any laws or [GitHub terms or policies](/en/site-policy). User-Generated Content displayed on GitHub Mobile may be subject to mobile app stores' additional terms.

### 3. Ownership of Content, Right to Post, and License Grants

You retain ownership of and responsibility for Your Content. If you're posting anything you did not create yourself or do not own the rights to, you agree that you are responsible for any Content you post; that you will only submit Content that you have the right to post; and that you will fully comply with any third party licenses relating to Content you post.

Because you retain ownership of and responsibility for Your Content, we need you to grant us — and other GitHub Users — certain legal permissions, listed in Sections D.4 — D.7. These license grants apply to Your Content. If you upload Content that already comes with a license granting GitHub the permissions we need to run our Service, no additional license is required. You understand that you will not receive any payment for any of the rights granted in Sections D.4 — D.7. The licenses you grant to us will end when you remove Your Content from our servers, unless other Users have forked it.

### 4. License Grant to Us

We need the legal right to do things like host Your Content, publish it, and share it. You grant us and our legal successors the right to store, archive, parse, and display Your Content, and make incidental copies, as necessary to provide the Service, including improving the Service over time. This license includes the right to do things like copy it to our database and make backups; show it to you and other users; parse it into a search index or otherwise analyze it on our servers; share it with other users; and perform it, in case Your Content is something like music or video.

This license does not grant GitHub the right to sell Your Content. It also does not grant GitHub the right to otherwise distribute or use Your Content outside of our provision of the Service, except that as part of the right to archive Your Content, GitHub may permit our partners to store and archive Your Content in public repositories in connection with the [GitHub Arctic Code Vault and GitHub Archive Program](https://archiveprogram.github.com/).

### 5. License Grant to Other Users

Any User-Generated Content you post publicly, including issues, comments, and contributions to other Users' repositories, may be viewed by others. By setting your repositories to be viewed publicly, you agree to allow others to view and "fork" your repositories (this means that others may make their own copies of Content from your repositories in repositories they control).

If you set your pages and repositories to be viewed publicly, you grant each User of GitHub a nonexclusive, worldwide license to use, display, and perform Your Content through the GitHub Service and to reproduce Your Content solely on GitHub as permitted through GitHub's functionality (for example, through forking). You may grant further rights if you [adopt a license](/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-license-to-a-repository#including-an-open-source-license-in-your-repository). If you are uploading Content you did not create or own, you are responsible for ensuring that the Content you upload is licensed under terms that grant these permissions to other GitHub Users.

### 6. Contributions Under Repository License

Whenever you add Content to a repository containing notice of a license, you license that Content under the same terms, and you agree that you have the right to license that Content under those terms. If you have a separate agreement to license that Content under different terms, such as a contributor license agreement, that agreement will supersede.

Isn't this just how it works already? Yep. This is widely accepted as the norm in the open-source community; it's commonly referred to by the shorthand "inbound=outbound". We're just making it explicit.

### 7. Moral Rights

You retain all moral rights to Your Content that you upload, publish, or submit to any part of the Service, including the rights of integrity and attribution. However, you waive these rights and agree not to assert them against us, to enable us to reasonably exercise the rights granted in Section D.4, but not otherwise.

To the extent this agreement is not enforceable by applicable law, you grant GitHub the rights we need to use Your Content without attribution and to make reasonable adaptations of Your Content as necessary to render the Website and provide the Service.

### 8. Access Reciprocity

By using automated means to access, collect, or otherwise use (“Access”) any publicly accessible Content from the Service for the purpose of developing or training any commercially available artificial intelligence model, machine learning system, or similar technology (a "Commercial AI System"), you hereby waive any and all policies, terms, conditions, or contractual provisions governing products, services, websites or datasets you own or operate that would otherwise prohibit, restrict, or place conditions upon GitHub's Access to any publicly accessible data, information or content associated with your products or services, including for the purpose of developing or training any Commercial AI System. You further agree not to impose technical or other targeted measures to restrict or retaliate against such Access.

This Section D.8 does not apply to Access solely for the purpose of academic research or if, on the date you Access the Content, the number of monthly active users of the products or services made available by you is less than 700 million in the preceding calendar month. For the purposes of this Section, "you" shall refer to you and any entity that directly or indirectly controls, is controlled by, or is under common control with you (affiliates).

## E. Private Repositories

**Short version:** *We treat the content of private repositories as confidential, and we only access it as described in our Privacy Statement—for security purposes, to assist the repository owner with a support matter, to maintain the integrity of the Service, to comply with our legal obligations, if we have reason to believe the contents are in violation of the law, or with your consent.*

### 1. Control of Private Repositories

Some Accounts may have private repositories, which allow the User to control access to Content.

### 2. Confidentiality of Private Repositories

GitHub considers the contents of private repositories to be confidential to you. GitHub will protect the contents of private repositories from unauthorized use, access, or disclosure in the same manner that we would use to protect our own confidential information of a similar nature and in no event with less than a reasonable degree of care.

### 3. Access

GitHub personnel may only access the content of your private repositories in the situations described in our [Privacy Statement](/en/site-policy/privacy-policies/github-privacy-statement#repository-contents).

You may choose to enable additional access to your private repositories. For example:

* You may enable various GitHub services or features that require additional rights to Your Content in private repositories. These rights may vary depending on the service or feature, but GitHub will continue to treat your private repository Content as confidential. If those services or features require rights in addition to those we need to provide the GitHub Service, we will provide an explanation of those rights.

Additionally, we may be [compelled by law](/en/site-policy/privacy-policies/github-privacy-statement#for-legal-disclosure) to disclose the contents of your private repositories.

GitHub will provide notice regarding our access to private repository content, unless [for legal disclosure](/en/site-policy/privacy-policies/github-privacy-statement#for-legal-disclosure), to comply with our legal obligations, or where otherwise bound by requirements under law, for automated scanning, or if in response to a security threat or other risk to security.

## F. Copyright Infringement and DMCA Policy

If you believe that content on our website violates your copyright, please contact us in accordance with our [Digital Millennium Copyright Act Policy](/en/site-policy/content-removal-policies/dmca-takedown-policy). If you are a copyright owner and you believe that content on GitHub violates your rights, please contact us via [our convenient DMCA form](https://github.com/contact/dmca) or by emailing <copyright@github.com>. There may be legal consequences for sending a false or frivolous takedown notice. Before sending a takedown request, you must consider legal uses such as fair use and licensed uses.

We will terminate the Accounts of [repeat infringers](/en/site-policy/content-removal-policies/dmca-takedown-policy#e-repeated-infringement) of this policy.

## G. Intellectual Property Notice

**Short version:** *We own the service and all of our content. In order for you to use our content, we give you certain rights to it, but you may only use our content in the way we have allowed.*

### 1. GitHub's Rights to Content

GitHub and our licensors, vendors, agents, and/or our content providers retain ownership of all intellectual property rights of any kind related to the Website and Service. We reserve all rights that are not expressly granted to you under this Agreement or by law. The look and feel of the Website and Service is copyright © GitHub, Inc. All rights reserved. You may not duplicate, copy, or reuse any portion of the HTML/CSS, JavaScript, or visual design elements or concepts without express written permission from GitHub.

### 2. GitHub Trademarks and Logos

If you’d like to use GitHub’s trademarks, you must follow all of our trademark guidelines, including those on our logos page: <https://github.com/logos>.

### 3. License to GitHub Policies

This Agreement is licensed under this [Creative Commons Zero license](https://creativecommons.org/publicdomain/zero/1.0/). For details, see our [site-policy repository](https://github.com/github/site-policy#license).

## H. API Terms

**Short version:** *You agree to these Terms of Service, plus this Section H, when using any of GitHub's APIs (Application Provider Interface), including use of the API through a third party product that accesses GitHub.*

Abuse or excessively frequent requests to GitHub via the API may result in the temporary or permanent suspension of your Account's access to the API. GitHub, in our sole discretion, will determine abuse or excessive usage of the API. We will make a reasonable attempt to warn you via email prior to suspension.

You may not share API tokens to exceed GitHub's rate limitations.

You may not use the API to download data or Content from GitHub for spamming purposes, including for the purposes of selling GitHub users' personal information, such as to recruiters, headhunters, and job boards.

All use of the GitHub API is subject to these Terms of Service and the [GitHub Privacy Statement](https://github.com/site/privacy).

GitHub may offer subscription-based access to our API for those Users who require high-throughput access or access that would result in resale of GitHub's Service.

## I. GitHub Additional Product Terms

**Short version:** *You need to follow certain specific terms and conditions for GitHub's various features and products, and you agree to the Supplemental Terms and Conditions when you agree to this Agreement.*

Some Service features may be subject to additional terms specific to that feature or product as set forth in the GitHub Additional Product Terms. By accessing or using the Services, you also agree to the [GitHub Additional Product Terms](/en/site-policy/github-terms/github-terms-for-additional-products-and-features).

## J. Beta Previews

**Short version:** *Beta Previews may not be supported or may change at any time. You may receive confidential information through those programs that must remain confidential while the program is private. We'd love your feedback to make our Beta Previews better.*

### 1. Subject to Change

Beta Previews may not be supported and may be changed at any time without notice. In addition, Beta Previews are not subject to the same security measures and auditing to which the Service has been and is subject. **By using a Beta Preview, you use it at your own risk.**

### 2. Confidentiality

As a user of Beta Previews, you may get access to special information that isn’t available to the rest of the world. Due to the sensitive nature of this information, it’s important for us to make sure that you keep that information secret.

**Confidentiality Obligations.** You agree that any non-public Beta Preview information we give you, such as information about a private Beta Preview, will be considered GitHub’s confidential information (collectively, “Confidential Information”), regardless of whether it is marked or identified as such. You agree to only use such Confidential Information for the express purpose of testing and evaluating the Beta Preview (the “Purpose”), and not for any other purpose. You should use the same degree of care as you would with your own confidential information, but no less than reasonable precautions to prevent any unauthorized use, disclosure, publication, or dissemination of our Confidential Information. You promise not to disclose, publish, or disseminate any Confidential Information to any third party, unless we don’t otherwise prohibit or restrict such disclosure (for example, you might be part of a GitHub-organized group discussion about a private Beta Preview feature).

**Exceptions.** Confidential Information will not include information that is: (a) or becomes publicly available without breach of this Agreement through no act or inaction on your part (such as when a private Beta Preview becomes a public Beta Preview); (b) known to you before we disclose it to you; (c) independently developed by you without breach of any confidentiality obligation to us or any third party; or (d) disclosed with permission from GitHub. You will not violate the terms of this Agreement if you are required to disclose Confidential Information pursuant to operation of law, provided GitHub has been given reasonable advance written notice to object, unless prohibited by law.

### 3. Feedback

We’re always trying to improve of products and services, and your feedback as a Beta Preview user will help us do that. If you choose to give us any ideas, know-how, algorithms, code contributions, suggestions, enhancement requests, recommendations or any other feedback for our products or services (collectively, “Feedback”), you acknowledge and agree that GitHub will have a royalty-free, fully paid-up, worldwide, transferable, sub-licensable, irrevocable and perpetual license to implement, use, modify, commercially exploit and/or incorporate the Feedback into our products, services, and documentation.

## K. Payment

**Short version:** *You are responsible for any fees associated with your use of GitHub. We are responsible for communicating those fees to you clearly and accurately, and letting you know well in advance if those prices change.*

### 1. Pricing

Our pricing and payment terms are available at [github.com/pricing](https://github.com/pricing). If you agree to a subscription price, that will remain your price for the duration of the payment term; however, prices are subject to change at the end of a payment term.

### 2. Upgrades, Downgrades, and Changes

* We will immediately bill you when you upgrade from the free plan to any paying plan.
* If you change from a monthly billing plan to a yearly billing plan, GitHub will bill you for a full year at the next monthly billing date.
* If you upgrade to a higher level of service, we will bill you for the upgraded plan immediately.
* You may change your level of service at any time by [choosing a plan option](https://github.com/pricing) or going into your [Billing settings](https://github.com/settings/billing). If you choose to downgrade your Account, you may lose access to Content, features, or capacity of your Account. Please see our section on [Cancellation](#l-cancellation-and-termination) for information on getting a copy of that Content.

### 3. Billing Schedule; No Refunds

**Payment Based on Plan** For monthly or yearly payment plans, the Service is billed in advance on a monthly or yearly basis respectively and is non-refundable. There will be no refunds or credits for partial months of service, downgrade refunds, or refunds for months unused with an open Account; however, the service will remain active for the length of the paid billing period. In order to treat everyone equally, no exceptions will be made.

**Payment Based on Usage** Some Service features are billed based on your usage. A limited quantity of these Service features may be included in your plan for a limited term without additional charge. If you choose to use paid Service features beyond the quantity included in your plan, you pay for those Service features based on your actual usage in the preceding month. Monthly payment for these purchases will be charged on a periodic basis in arrears. See [GitHub Additional Product Terms for Details](/en/site-policy/github-terms/github-terms-for-additional-products-and-features).

**Invoicing** For invoiced Users, User agrees to pay the fees in full, up front without deduction or setoff of any kind, in U.S. Dollars. User must pay the fees within thirty (30) days of the GitHub invoice date. Amounts payable under this Agreement are non-refundable, except as otherwise provided in this Agreement. If User fails to pay any fees on time, GitHub reserves the right, in addition to taking any other action at law or equity, to (i) charge interest on past due amounts at 1.0% per month or the highest interest rate allowed by law, whichever is less, and to charge all expenses of recovery, and (ii) terminate the applicable order form. User is solely responsible for all taxes, fees, duties and governmental assessments (except for taxes based on GitHub's net income) that are imposed or become due in connection with this Agreement.

### 4. Authorization

By agreeing to these Terms, you are giving us permission to charge your on-file credit card, PayPal account, or other approved methods of payment for fees that you authorize for GitHub.

### 5. Responsibility for Payment

You are responsible for all fees, including taxes, associated with your use of the Service. By using the Service, you agree to pay GitHub any charge incurred in connection with your use of the Service. If you dispute the matter, contact us through the [GitHub Support portal](https://support.github.com/). You are responsible for providing us with a valid means of payment for paid Accounts. Free Accounts are not required to provide payment information.

## L. Cancellation and Termination

**Short version:** *You may close your Account at any time. If you do, we'll treat your information responsibly.*

### 1. Account Cancellation

It is your responsibility to properly cancel your Account with GitHub. You can [cancel your Account at any time](/en/billing/managing-the-plan-for-your-github-account/downgrading-your-accounts-plan) by going into your Settings in the global navigation bar at the top of the screen. The Account screen provides a simple, no questions asked cancellation link. We are not able to cancel Accounts in response to an email or phone request.

### 2. Upon Cancellation

We will retain and use your information as necessary to comply with our legal obligations, resolve disputes, and enforce our agreements, but barring legal requirements, we will delete your full profile and the Content of your repositories within 90 days of cancellation or termination (though some information may remain in encrypted backups). This information cannot be recovered once your Account is canceled.

We will not delete Content that you have contributed to other Users' repositories or that other Users have forked.

Upon request, we will make a reasonable effort to provide an Account owner with a copy of your lawful, non-infringing Account contents after Account cancellation, termination, or downgrade. You must make this request within 90 days of cancellation, termination, or downgrade.

### 3. GitHub May Terminate

GitHub has the right to suspend or terminate your access to all or any part of the Website at any time, with or without cause, with or without notice, effective immediately. GitHub reserves the right to refuse service to anyone for any reason at any time.

### 4. Survival

All provisions of this Agreement which, by their nature, should survive termination *will* survive termination — including, without limitation: ownership provisions, warranty disclaimers, indemnity, and limitations of liability.

## M. Communications with GitHub

**Short version:** *We use email and other electronic means to stay in touch with our users.*

### 1. Electronic Communication Required

For contractual purposes, you (1) consent to receive communications from us in an electronic form via the email address you have submitted or via the Service; and (2) agree that all Terms of Service, agreements, notices, disclosures, and other communications that we provide to you electronically satisfy any legal requirement that those communications would satisfy if they were on paper. This section does not affect your non-waivable rights.

### 2. Legal Notice to GitHub Must Be in Writing

Communications made through email or GitHub Support's messaging system will not constitute legal notice to GitHub or any of its officers, employees, agents or representatives in any situation where notice to GitHub is required by contract or any law or regulation. Legal notice to GitHub must be in writing and [served on GitHub's legal agent](/en/site-policy/other-site-policies/guidelines-for-legal-requests-of-user-data#submitting-requests).

### 3. No Phone Support

GitHub only offers support via email, in-Service communications, and electronic messages. We do not offer telephone support.

## N. Disclaimer of Warranties

**Short version:** *We provide our service as is, and we make no promises or guarantees about this service. Please read this section carefully; you should understand what to expect.*

GitHub provides the Website and the Service “as is” and “as available,” without warranty of any kind. Without limiting this, we expressly disclaim all warranties, whether express, implied or statutory, regarding the Website and the Service including without limitation any warranty of merchantability, fitness for a particular purpose, title, security, accuracy and non-infringement.

GitHub does not warrant that the Service will meet your requirements; that the Service will be uninterrupted, timely, secure, or error-free; that the information provided through the Service is accurate, reliable or correct; that any defects or errors will be corrected; that the Service will be available at any particular time or location; or that the Service is free of viruses or other harmful components. You assume full responsibility and risk of loss resulting from your downloading and/or use of files, information, content or other material obtained from the Service.

## O. Limitation of Liability

**Short version:** *We will not be liable for damages or losses arising from your use or inability to use the service or otherwise arising under this agreement. Please read this section carefully; it limits our obligations to you.*

You understand and agree that we will not be liable to you or any third party for any loss of profits, use, goodwill, or data, or for any incidental, indirect, special, consequential or exemplary damages, however arising, that result from

<!-- markdownlint-disable GHD034 -->

* the use, disclosure, or display of your User-Generated Content;
* your use or inability to use the Service;
* any modification, price change, suspension or discontinuance of the Service;
* the Service generally or the software or systems that make the Service available;
* unauthorized access to or alterations of your transmissions or data;
* statements or conduct of any third party on the Service;
* any other user interactions that you input or receive through your use of the Service; or
* any other matter relating to the Service.

<!-- markdownlint-enable GHD034 -->

Our liability is limited whether or not we have been informed of the possibility of such damages, and even if a remedy set forth in this Agreement is found to have failed of its essential purpose. We will have no liability for any failure or delay due to matters beyond our reasonable control.

## P. Release and Indemnification

**Short version:** *You are responsible for your use of the service. If you harm someone else or get into a dispute with someone else, we will not be involved.*

If you have a dispute with one or more Users, you agree to release GitHub from any and all claims, demands and damages (actual and consequential) of every kind and nature, known and unknown, arising out of or in any way connected with such disputes.

You agree to indemnify us, defend us, and hold us harmless from and against any and all claims, liabilities, and expenses, including attorneys’ fees, arising out of your use of the Website and the Service, including but not limited to your violation of this Agreement, provided that GitHub (1) promptly gives you written notice of the claim, demand, suit or proceeding; (2) gives you sole control of the defense and settlement of the claim, demand, suit or proceeding (provided that you may not settle any claim, demand, suit or proceeding unless the settlement unconditionally releases GitHub of all liability); and (3) provides to you all reasonable assistance, at your expense.

## Q. Changes to These Terms

**Short version:** *We want our users to be informed of important changes to our terms, but some changes aren't that important — we don't want to bother you every time we fix a typo. So while we may modify this agreement at any time, we will notify users of any material changes and give you time to adjust to them.*

We reserve the right, at our sole discretion, to amend these Terms of Service at any time and will update these Terms of Service in the event of any such amendments. We will notify our Users of material changes to this Agreement, such as price increases, at least 30 days prior to the change taking effect by posting a notice on our Website or sending email to the primary email address specified in your GitHub account. Customer's continued use of the Service after those 30 days constitutes agreement to those revisions of this Agreement. For any other modifications, your continued use of the Website constitutes agreement to our revisions of these Terms of Service. You can view all changes to these Terms in our [Site Policy](https://github.com/github/site-policy) repository.

We reserve the right at any time and from time to time to modify or discontinue, temporarily or permanently, the Website (or any part of it) with or without notice.

## R. Miscellaneous

### 1. Governing Law

Except to the extent applicable law provides otherwise, this Agreement between you and GitHub and any access to or use of the Website or the Service are governed by the federal laws of the United States of America and the laws of the State of California, without regard to conflict of law provisions. You and GitHub agree to submit to the exclusive jurisdiction and venue of the courts located in the City and County of San Francisco, California. However, any claim for injunctive relief with respect to a violation of section D.8 may be brought in any jurisdiction.

### 2. Non-Assignability

GitHub may assign or delegate these Terms of Service and/or the [GitHub Privacy Statement](https://github.com/site/privacy), in whole or in part, to any person or entity at any time with or without your consent, including the license grant in Section D.4. You may not assign or delegate any rights or obligations under the Terms of Service or Privacy Statement without our prior written consent, and any unauthorized assignment and delegation by you is void.

### 3. Section Headings and Summaries

Throughout this Agreement, each section includes titles and brief summaries of the following terms and conditions. These section titles and brief summaries are not legally binding.

### 4. Severability, No Waiver, and Survival

If any part of this Agreement is held invalid or unenforceable, that portion of the Agreement will be construed to reflect the parties’ original intent. The remaining portions will remain in full force and effect. Any failure on the part of GitHub to enforce any provision of this Agreement will not be considered a waiver of our right to enforce such provision. Our rights under this Agreement will survive any termination of this Agreement.

### 5. Amendments; Complete Agreement

This Agreement may only be modified by a written amendment signed by an authorized representative of GitHub, or by the posting by GitHub of a revised version in accordance with [Section Q. Changes to These Terms](#q-changes-to-these-terms). These Terms of Service, together with the GitHub Privacy Statement, represent the complete and exclusive statement of the agreement between you and us. This Agreement supersedes any proposal or prior agreement oral or written, and any other communications between you and GitHub relating to the subject matter of these terms including any confidentiality or nondisclosure agreements.

### 6. Questions

Questions about the Terms of Service? Contact us through the [GitHub Support portal](https://support.github.com/).# GitHub General Privacy Statement

<!-- markdownlint-disable search-replace -->

## GitHub Privacy Statement

Effective date: February 1, 2024

Welcome to the GitHub Privacy Statement. This is where we describe how we handle your “Personal Data”, which is information that is directly linked or can be linked to you. It applies to the Personal Data that GitHub, Inc. or GitHub B.V., processes as the “Data Controller” when you interact with websites, applications, and services that display this Statement (collectively, “Services”). This Statement does not apply to services or products that do not display this Statement, such as Previews, where relevant.

### End User Notice: Organization-Provided GitHub Accounts

When a school or employer supplies your GitHub account, they assume the role of Data Controller for most Personal Data used in our Services. This enables them to:

* Manage and administer your GitHub account, including adjusting privacy settings.
* Access and utilize your Personal Data, which includes details on how you use the Services, as well as your content and files.

Should you access a GitHub Service through an account provided by an organization, such as your employer or school, the organization becomes the Data Controller, and this Privacy Statement's direct applicability to you changes. Even so, GitHub remains dedicated to preserving your privacy rights. In such circumstances, GitHub functions as a Data Processor, adhering to the Data Controller's instructions regarding your Personal Data's processing. A Data Protection Agreement governs the relationship between GitHub and the Data Controller. For further details regarding their privacy practices, please refer to the privacy statement of the organization providing your account.

In cases where your organization grants access to GitHub products, GitHub acts as the Data Controller solely for specific processing activities. These activities are clearly defined in a contractual agreement with your organization, known as a Data Protection Agreement. You can review our standard Data Protection Agreement at [GitHub Data Protection Agreement](https://github.com/customer-terms/github-data-protection-agreement). For those limited purposes, this Statement governs the handling of your Personal Data. For all other aspects of GitHub product usage, your organization's policies apply.

### Third Party Access and Data Protection

When you use third-party extensions, integrations, or follow references and links within our Services, the privacy policies of these third parties apply to any Personal Data you provide or consent to share with them. Their privacy statements will govern how this data is processed.

## Personal Data We Collect

Personal Data is collected from you directly, automatically from your device, and also from third parties. The Personal Data GitHub processes when you use the Services depends on variables like how you interact with our Services (such as through web interfaces, desktop or mobile applications), the features you use (such as pull requests, Codespaces, or GitHub Copilot) and your method of accessing the Services (your preferred IDE). Below, we detail the information we collect through each of these channels:

### From You

* Account Data: We collect certain information when you open an account such as your GitHub handle, name, email address, password, payment information and transaction information.
* User Content and Files: When you use our Services, we collect Personal Data included as part of the information you provide such as code, inputs, text, documents, images, or feedback.
* Demographic information: In some cases, you provide us with ethnicity, gender, or similar demographic details.
* Feedback Data: This consists of information you submit through surveys, reviews, or interactive features.
* Payment Information: For paid subscriptions, we collect details like name, billing address, and payment specifics.
* Profile Information: We collect information to create a user profile, which may include a photo, additional email addresses, job title, or biography.
* Sales and Marketing Data: This includes information provided for promotional communications, such as name, email address, and company name.
* Support Data: When you seek customer support, we collect details like code, text, or multimedia files.

### Automatically

* Buttons, Tools, and Content from Other Companies: Our Services may contain links or buttons that lead to third-party services like Twitter or LinkedIn. Use of these features may result in data collection. Engaging with these buttons, tools, or content may automatically send certain browser information to these companies. Please review the privacy statements of these companies for more information.
* Essential Cookies and Similar Tracking Technologies: We use cookies and similar technologies to provide essential functionality like storing settings and recognizing you while using our Services.
* Non-essential Cookies: Depending on your jurisdiction, we may use online analytics products that use cookies to help us analyze how de-identified users use our Services and to enhance your experience when you use the Services. We may also employ third-party Cookies to gather data for interest-based advertising. In some jurisdictions, we only use non-essential cookies after obtaining your consent. See [this](#what-are-your-cookie-choices-and-controls) section for more details and control options.
* Email Marketing Interactions: Our emails may have web beacons that offer information on your device type, email client, email reception, opens, and link clicks.
* Geolocation Information: Depending on the Service's functionality, we collect regional geolocation data.
* Service Usage Information: We collect data about your interactions with the Services, such as IP address, device information, session details, date and time of requests, device type and ID, operating system and application version, information related to your contributions to repositories, and performance of specific features or Services.
* Website Usage Data: We automatically log data about your Website interactions, including the referring site, date and time of visit, pages viewed, and links clicked.

### From Third Parties

* Information from Other Users of the Services: Other users may share information about you when they submit issues and comments. We may also receive information about you if you are identified as a representative or administrator on your company's account.
* Publicly Available Sources: We may acquire information about you from publicly available sources like public GitHub repositories.
* Services you linked to your GitHub account: When you or your administrator integrate third-party apps or services with our Services, we receive information based on your settings with those services. This can include details like your name and email from services like Google for authentication. The information we receive depends on the third-party's settings and privacy policies. Always review these to understand what data is shared with our Services.
* Vendors, Partners, and Affiliates: We may receive information about you from third parties, like vendors, resellers, partners, or affiliates for the purposes outlined in this statement.

## Processing Purposes: How We Use Your Personal Data

The Personal Data we process depends on your interaction and access methods with our Services, including the interfaces (web, desktop, mobile apps), features used (pull requests, Codespaces, GitHub Copilot), and your preferred access tools (like your IDE). This section details all the potential ways GitHub may process your Personal Data:

* Business Operations: We use Personal Data for activities like billing, accounting, and compensation. This includes creating aggregated statistical data for internal reporting, financial reporting, revenue planning, capacity planning, and forecast modeling (including product strategy).
* Communication: We use Personal Data to inform you about new Services, features, offers, promotions, and other pertinent information. This also includes sending confirmations, invoices, technical notices, updates, security alerts, and administrative messages.
* Inference: We generate new information from other data we collect to derive likely preferences or other characteristics. For instance, we infer your general geographic location based on your IP address.
* Personalization: We use Personal Data to customize the Service to your preferences, to evaluate the effectiveness of enterprise business ads and promotional communications, and to ensure a seamless and consistent user experience.
* Safety and Security: To promote safety, integrity, and security across our Services, we process Personal Data, using both automated and, at times, manual techniques for abuse detection, prevention, and violations of terms of service.
* Service Provision: We use Personal Data to deliver and update our Services as configured and used by You, and to make ongoing personalized experiences and recommendations.
* Troubleshooting: We use Personal Data to identify and resolve technical issues.
* Ongoing Service Performance: Personal Data helps us keep the Services up to date and performant, and meet user productivity, reliability, efficacy, quality, privacy, accessibility and security needs.
* Complying with and resolving legal obligations: including responding to Data Subject Requests for Personal Data processed by GitHub as Controller (for example website data), tax requirements, agreements and disputes.
* Delivering Professional Services: We use Personal Data to deliver training, consulting or implementation (“Professional Services”). This includes providing technical support, professional planning, advice, guidance, data migration, deployment, and solution/software development services.
* Improving Professional Services: Enhancing delivery, efficacy, quality, and security of Professional Services and the underlying product(s) based on issues identified while providing Professional Services, including fixing software defects, and otherwise keeping the Professional Services up to date and performant.

When carrying out these activities, GitHub practices data minimization and uses the minimum amount of Personal Information required.

## Sharing of Personal Data

We may share Personal Data with the following recipients:

* Abuse and Fraud Prevention Entities: We may disclose Personal Data based on a good faith belief it is needed to prevent fraud, abuse, or attacks on our Services, or to protect the safety of GitHub and our users.
* Affiliates: Personal Data may be shared with GitHub affiliates, including Microsoft, to facilitate customer service, marketing and advertising, order fulfillment, billing, technical support, and legal and compliance obligations. Our affiliates may only use the Personal Data in a manner consistent with this Privacy Statement.
* GitHub Organization Accounts: If an organization adds you to their GitHub account, we might share Personal Data with that organization to fulfill the commercial relationship. In such a case, your use of the Services is protected by a data protection agreement and terms between your organization and GitHub
* Competent Authorities: We may disclose Personal Data to authorized law enforcement, regulators, courts, or other public authorities in response to lawful requests or to protect our rights and safety. Please refer to our [Guidelines for Legal Requests of User Data](https://docs.github.com/en/site-policy/other-site-policies/guidelines-for-legal-requests-of-user-data) for more information.
* Corporate Transaction Entities: we might disclose Personal Data within the limits of the law and in accordance with this Privacy Statement for strategic business transactions such as sales or a merger.
* Partners and Resellers: We cooperate with third-parties that offer sales, consulting, support, and technical services for our Services. We may share your data with these partners and resellers where allowed, and with your consent when required.
* Subprocessors and Service Providers: We may use vendors to provide services on our behalf, including hosting, marketing, advertising, social, analytics, support ticketing, credit card processing, or security services. They are bound by contractual obligations to ensure the security, privacy, and confidentiality of your information. Please visit <https://docs.github.com/en/site-policy/privacy-policies/github-subprocessors> to see our list of Subprocessors.
* Visual Studio Code (GitHub Codespaces): GitHub Codespaces and github.dev offer Visual Studio Code in a web browser, where some telemetry is collected by default. Details on telemetry collection are on the [VS Code website](https://code.visualstudio.com/docs/configure/telemetry). To opt out, go to File > Preferences > Settings in the top left menu of VS Code. Opting out will sync this preference across all future web sessions in GitHub Codespaces and github.dev.
* Other Third-party Applications: Upon your instruction, we may share Personal Data with third-party applications available on our Marketplace. You are responsible for the data you instruct us to share with these applications.
* Other Users and the Public: Depending on your account settings, we may share Personal Data with other users of the Services and the public. You control what information is made public. To adjust your settings, visit User Settings in your profile. Please be aware that any information you share in a collaborative context may become publicly accessible.

## Private repositories: GitHub Access

If your GitHub account has private repositories, you control the access to that information. GitHub personnel does not access private repository information without your consent except as provided in this Privacy Statement and for:

<!-- markdownlint-disable GHD034 -->

* security purposes
* automated scanning or manual review for known vulnerabilities, active malware, or other content known to violate our Terms of Service
* to assist the repository owner with a support matter
* to maintain the integrity of the Services, or
* to comply with our legal obligations if we have reason to believe the contents are in violation of the law.

<!-- markdownlint-enable GHD034 -->

GitHub will provide you with notice regarding private repository access unless doing so is prohibited by law or if GitHub acted in response to a security threat or other risk to security.

## Lawful Bases for Processing Personal Data (Applicable to EEA and UK End Users)

GitHub processes Personal Data in compliance with the GDPR, ensuring a lawful basis for each processing activity. The basis varies depending on the data type and the context, including how you access the services. Our processing activities typically fall under these lawful bases:

* Contractual Necessity: Processing is required to fulfill our contractual duties to you, in accordance with the GitHub Terms of Service.
* Legal Obligation: We process data when it's necessary to comply with applicable laws or to protect the rights, safety, and property of GitHub, our affiliates, users, or third parties.
* Legitimate Interests: We process data for purposes that are in our legitimate interests, such as securing our Services, communicating with you, and improving our Services. This is done only when these interests are not overridden by your data protection rights or your fundamental rights and freedoms.
* Consent: We process data when you have explicitly consented to such processing. When we rely on consent as the legal basis, you have the right to withdraw your consent for data processing at any time. The procedures for withdrawal are detailed in this Statement and available on our website.

## Your Privacy Rights

Depending on your residence location, you may have specific legal rights regarding your Personal Data:

* The right to access the data collected about you
* The right to request detailed information about the specific types of Personal Data we've collected over the past 12 months, including data disclosed for business purposes
* The right to rectify or update inaccurate or incomplete Personal Data under certain circumstances
* The right to erase or limit the processing of your Personal Data under specific conditions
* The right to object to the processing of your Personal Data, as allowed by applicable law
* The right to withdraw consent, where processing is based on your consent
* The right to receive your collected Personal Data in a structured, commonly used, and machine-readable format to facilitate its transfer to another company, where technically feasible

To exercise these rights, please send an email to privacy\[at]github\[dot]com and follow the instructions provided. To verify your identity for security, we may request extra information before addressing your data-related request. Please contact our Data Protection Officer at dpo\[at]github\[dot]com for any feedback or concerns. Depending on your region, you have the right to complain to your local Data Protection Authority. European users can find authority contacts on the European Data Protection Board website, and UK users on the Information Commissioner’s Office website.

We aim to promptly respond to requests in compliance with legal requirements. Please note that we may retain certain data as necessary for legal obligations or for establishing, exercising, or defending legal claims.

## International data transfers

GitHub stores and processes Personal Data in a variety of locations, including your local region, the United States, and other countries where GitHub, its affiliates, subsidiaries, or subprocessors have operations. We transfer Personal Data from the European Union, the United Kingdom, and Switzerland to countries that the European Commission has not recognized as having an adequate level of data protection. When we engage in such transfers, we generally rely on the standard contractual clauses published by the European Commission under [Commission Implementing Decision 2021/914](https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj), to help protect your rights and enable these protections to travel with your data. To learn more about the European Commission’s decisions on the adequacy of the protection of personal data in the countries where GitHub processes personal data, see this article on the [European Commission website](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/adequacy-decisions_en).

## Data Privacy Framework (DPF)

GitHub also complies with the EU-U.S. Data Privacy Framework (EU-U.S. DPF), the UK Extension to the EU-U.S. DPF, and the Swiss-U.S. Data Privacy Framework (Swiss-U.S. DPF) as set forth by the U.S. Department of Commerce. GitHub has certified to the U.S. Department of Commerce that it adheres to the EU-U.S. Data Privacy Framework Principles (EU-U.S. DPF Principles) with regard to the processing of personal data received from the European Union in reliance on the EU-U.S. DPF and from the United Kingdom (and Gibraltar) in reliance on the UK Extension to the EU-U.S. DPF. GitHub has certified to the U.S. Department of Commerce that it adheres to the Swiss-U.S. Data Privacy Framework Principles (Swiss-U.S. DPF Principles) with regard to the processing of personal data received from Switzerland in reliance on the Swiss-U.S. DPF. If there is any conflict between the terms in this privacy statement and the EU-U.S. DPF Principles and/or the Swiss-U.S. DPF Principles, the Principles shall govern. To learn more about the Data Privacy Framework (DPF) program, and to view our certification, please visit <https://www.dataprivacyframework.gov/>.

GitHub has the responsibility for the processing of Personal Data it receives under the Data Privacy Framework (DPF) Principles and subsequently transfers to a third party acting as an agent on GitHub’s behalf. GitHub shall remain liable under the DPF Principles if its agent processes such Personal Data in a manner inconsistent with the DPF Principles, unless the organization proves that it is not responsible for the event giving rise to the damage.

### Dispute resolution process

In compliance with the EU-U.S. DPF, the UK Extension to the EU-U.S. DPF, and the Swiss-U.S. DPF, GitHub commits to resolve DPF Principles-related complaints about our collection and use of your personal information. EU, UK, and Swiss individuals with inquiries or complaints regarding our handling of personal data received in reliance on the EU-U.S. DPF, the UK Extension, and the Swiss-U.S. DPF should first contact GitHub at: dpo\[at]github\[dot]com.

If you do not receive timely acknowledgment of your DPF Principles-related complaint from us, or if we have not addressed your DPF Principles-related complaint to your satisfaction, please visit <https://go.adr.org/dpf_irm.html> for more information or to file a complaint. The services of the International Centre for Dispute Resolution are provided at no cost to you.

An individual has the possibility, under certain conditions, to invoke binding arbitration for complaints regarding DPF compliance not resolved by any of the other DPF mechanisms. For additional information visit <https://www.dataprivacyframework.gov/framework-article/ANNEX-I-introduction>.

### Government Enforcement

GitHub is subject to the investigatory and enforcement powers of the Federal Trade Commission (FTC). Under Section 5 of the Federal Trade Commission Act (15 U.S.C. § 45), an organization's failure to abide by commitments to implement the DPF Principles may be challenged as deceptive by the FTC. The FTC has the power to prohibit such misrepresentations through administrative orders or by seeking court orders.

## Security and Retention

GitHub uses appropriate administrative, technical, and physical security controls to protect your Personal Data. We’ll retain your Personal Data as long as your account is active and as needed to fulfill contractual obligations, comply with legal requirements, resolve disputes, and enforce agreements. The retention duration depends on the purpose of data collection and any legal obligations.

## Security

GitHub uses administrative, technical, and physical security controls where appropriate to protect your Personal Data.

## Contact Us

Contact us via our contact form or by emailing our Data Protection Officer at dpo\[at]github\[dot]com.
Our addresses are:

GitHub B.V.
Prins Bernhardplein 200, Amsterdam
1097JB
The Netherlands

GitHub, Inc.
88 Colin P. Kelly Jr. St.
San Francisco, CA 94107
United States

## Information for Minors

Our Services are not intended for individuals under the age of 13. We do not intentionally gather Personal Data from such individuals. If you become aware that a minor has provided us with Personal Data, please [notify us](https://support.github.com/contact/privacy).

## Changes to Our Privacy Statement

GitHub may periodically revise this Privacy Statement. If there are material changes to the statement, we will provide at least 30 days prior notice by updating our website or sending an email to your primary email address associated with your GitHub account.

## Translations

Below are translations of this document into other languages. In the event of any conflict, uncertainty, or apparent inconsistency between any of those versions and the English version, this English version is the controlling version.

### French

Cliquez ici pour obtenir la version française: [Déclaration de confidentialité de GitHub (PDF)](/assets/images/help/site-policy/github-privacy-statement\(07.22.20\)\(fr\).pdf).

### Other translations

For translations of this statement into other languages, please visit <https://docs.github.com/> and select a language from the drop-down menu under “English.”

## Our use of cookies and tracking technologies

### Cookies and tracking technologies

GitHub uses cookies to provide, secure and improve our Service or to develop new features and functionality of our Service. For example, we use them to (i) keep you logged in, (ii) remember your preferences, (iii) identify your device for security and fraud purposes, including as needed to maintain the integrity of our Service, (iv) compile statistical reports, and (v) provide information and insight for future development of GitHub. We provide more information about [cookies on GitHub](/en/site-policy/privacy-policies/github-cookies) that describes the cookies we set, the needs we have for those cookies, and the expiration of such cookies.

For Enterprise Marketing Pages, we may also use non-essential cookies to (i) gather information about enterprise users’ interests and online activities to personalize their experiences, including by making the ads, content, recommendations, and marketing seen or received more relevant and (ii) serve and measure the effectiveness of targeted advertising and other marketing efforts. If you disable the non-essential cookies on the Enterprise Marketing Pages, the ads, content, and marketing you see may be less relevant.

Our emails to users may contain a pixel tag, which is a small, clear image that can tell us whether or not you have opened an email and what your IP address is. We use this pixel tag to make our email communications more effective and to make sure we are not sending you unwanted email.

The length of time a cookie will stay on your browser or device depends on whether it is a “persistent” or “session” cookie. Session cookies will only stay on your device until you stop browsing. Persistent cookies stay until they expire or are deleted. The expiration time or retention period applicable to persistent cookies depends on the purpose of the cookie collection and tool used. You may be able to delete cookie data. For more information, see [GitHub General Privacy Statement](/en/site-policy/privacy-policies/github-privacy-statement#what-are-your-cookie-choices-and-controls).

#### What are cookies and similar technologies?

We use cookies and similar technologies, such as web beacons, local storage, and mobile analytics, to operate and provide our Services. When visiting Enterprise Marketing Pages, like resources.github.com, these and additional cookies, like advertising IDs, may be used for sales and marketing purposes.

Cookies are small text files stored by your browser on your device. A cookie can later be read when your browser connects to a web server in the same domain that placed the cookie. The text in a cookie contains a string of numbers and letters that may uniquely identify your device and can contain other information as well. This allows the web server to recognize your browser over time, each time it connects to that web server.

Web beacons are electronic images (also called “single-pixel” or “clear GIFs”) that are contained within a website or email. When your browser opens a webpage or email that contains a web beacon, it automatically connects to the web server that hosts the image (typically operated by a third party). This allows that web server to log information about your device and to set and read its own cookies. In the same way, third-party content on our websites (such as embedded videos, plug-ins, or ads) results in your browser connecting to the third-party web server that hosts that content.

Mobile identifiers for analytics can be accessed and used by apps on mobile devices in much the same way that websites access and use cookies. When visiting Enterprise Marketing pages, like resources.github.com, on a mobile device these may allow us and our third-party analytics and advertising partners to collect data for sales and marketing purposes.

We may also use so-called “flash cookies” (also known as “Local Shared Objects” or “LSOs”) to collect and store information about your use of our Services. Flash cookies are commonly used for advertisements and videos.

#### How do we and our partners use cookies and similar technologies?

The GitHub Services use cookies and similar technologies for a variety of purposes, including to store your preferences and settings, enable you to sign-in, analyze how our Services perform, track your interaction with the Services, develop inferences, combat fraud, and fulfill other legitimate purposes. Some of these cookies and technologies may be provided by third parties, including service providers and advertising partners. For example, our analytics and advertising partners may use these technologies in our Services to collect personal information (such as the pages you visit, the links you click on, and similar usage information, identifiers, and device information) related to your online activities over time and across Services for various purposes, including targeted advertising. GitHub will place non-essential cookies on pages where we market products and services to enterprise customers, for example, on resources.github.com.

We and/or our partners also share the information we collect or infer with third parties for these purposes.

The table below provides additional information about how we use different types of cookies:

| Purpose          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Required Cookies | GitHub uses required cookies to perform essential website functions and to provide the services. For example, cookies are used to log you in, save your language preferences, provide a shopping cart experience, improve performance, route traffic between web servers, detect the size of your screen, determine page load times, improve user experience, and for audience measurement. These cookies are necessary for our websites to work.    |
| Analytics        | We allow third parties to use analytics cookies to understand how you use our websites so we can make them better. For example, cookies are used to gather information about the pages you visit and how many clicks you need to accomplish a task. We also use some analytics cookies to provide personalized advertising.                                                                                                                          |
| Social Media     | GitHub and third parties use social media cookies to show you ads and content based on your social media profiles and activity on GitHub’s websites. This ensures that the ads and content you see on our websites and on social media will better reflect your interests. This also enables third parties to develop and improve their products, which they may use on websites that are not owned or operated by GitHub.                           |
| Advertising      | In addition, GitHub and third parties use advertising cookies to show you new ads based on ads you've already seen. Cookies also track which ads you click or purchases you make after clicking an ad. This is done both for payment purposes and to show you ads that are more relevant to you. For example, cookies are used to detect when you click an ad and to show you ads based on your social media interests and website browsing history. |

#### What are your cookie choices and controls?

You have several options to disable non-essential cookies:

1. **Specifically on GitHub Enterprise Marketing Pages**

   Any GitHub page that serves non-essential cookies will have a link in the page’s footer to cookie settings. You can express your preferences at any time by clicking on that linking and updating your settings.

   Some users will also be able to manage non-essential cookies via a cookie consent banner, including the options to accept, manage, and reject all non-essential cookies.
2. **Generally for all websites**
   You can control the cookies you encounter on the web using a variety of widely-available tools. For example:

* If your browser sends a [Do Not Track](https://en.wikipedia.org/wiki/Do_Not_Track) (DNT) signal, GitHub will not set non-essential cookies and will not load third party resources which set non-essential cookies.
* Many browsers provide cookie controls which may limit the types of cookies you encounter online. Check out the documentation for your browser to learn more.
* If you enable a browser extension designed to block tracking, such as [Privacy Badger](https://en.wikipedia.org/wiki/Privacy_Badger), non-essential cookies set by a website or third parties may be disabled.
* If you enable a browser extension designed to block unwanted content, such as [uBlock Origin](https://en.wikipedia.org/wiki/UBlock_Origin), non-essential cookies will be disabled to the extent that content that sets non-essential cookies will be blocked.
* You may use the Global Privacy Control (GPC) to communicate your privacy preferences. If GitHub detects the GPC signal from your device, GitHub will not share your data (we do not sell your data). To learn more, visit [Global Privacy Control — Take Control Of Your Privacy](https://globalprivacycontrol.org/)
* Advertising controls. Our advertising partners may participate in associations that provide simple ways to opt out of ad targeting, which you can access at:
* United States: [NAI](http://optout.networkadvertising.org) and [DAA](http://optout.aboutads.info/)
* Canada: [Digital Advertising Alliance of Canada](https://youradchoices.ca/)
* Europe: [European Digital Advertising Alliance](http://www.youronlinechoices.com/)

These choices are specific to the browser you are using. If you access our Services from other devices or browsers, take these actions from those systems to ensure your choices apply to the data collected when you use those systems.

## US State Specific Information

This section provides extra information specifically for residents of certain US states that have distinct data privacy laws and regulations. These laws may grant specific rights to residents of these states when the laws come into effect. This section uses the term “personal information” as an equivalent to the term “Personal Data.”

### Privacy Rights

These rights are common to the US State privacy laws:

* Right to Knowledge and Correction: You have the right to request details on the specific personal information we’ve collected about you and the right to correct inaccurate information. You can exercise this right by contacting us. You can also access and edit basic account information in your settings.
* Right to Know Data Recipients: We share your information with service providers for legitimate business operations, such as data storage and hosting. For more details, please see “Sharing Your Information” below.
* Right to request Deletion: You reserve the right to request the deletion of your data, barring a few exceptions. Such exceptions include circumstances where we are required to retain data to comply with legal obligations, detect fraudulent activity, investigate reports of abuse or other violations of our Terms of Service, or rectify security issues. Upon receiving your verified request, we will promptly delete your personal information (unless an exception applies), and instruct our service providers to do the same. We employ brief retention terms by design.
* Right to a Timely Response: You are allowed to make two free requests in any 12-month period. We commit to responding to your request within 45 days. In complex cases, we may extend our response time by an additional 45 days.
* Non-Discrimination: We will not hold it against you when you exercise any of your rights. On the contrary, we encourage you to review your privacy settings closely and contact us with any questions.

### Notice of Collection of Personal Information

We may collect various categories of personal information about our website visitors and users of "Services" which includes GitHub applications, software, products, or services. That information includes identifiers/contact information, demographic information, payment information, commercial information, internet or electronic network activity information, geolocation data, audio, electronic, visual, or similar information, and inferences drawn from such information.

We collect this information for various purposes. This includes identifying accessibility gaps and offering targeted support, fostering diversity and representation, providing services, troubleshooting, conducting business operations such as billing and security, improving products and supporting research, communicating important information, ensuring personalized experiences, and promoting safety and security.

### Exercising your Privacy Rights

To make an access, deletion, correction, or opt-out request, please send an email to privacy\[at]github\[dot]com and follow the instructions provided. We may need to verify your identity before processing your request. If you choose to use an authorized agent to submit a request on your behalf, please ensure they have your signed permission or power of attorney as required.

To opt out of the sharing of your personal information, you can click on the "Do Not Share My Personal Information" link on the footer of our Websites or use the Global Privacy Control ("GPC") if available. Authorized agents can also submit opt-out requests on your behalf.

### California

#### Mandatory Disclosures

We also make the following disclosures for purposes of compliance with California privacy law:

* We collected the following categories of personal information in the last 12 months: identifiers/contact information, demographic information (such as gender), payment card information associated with you, commercial information, Internet or other electronic network activity information, geolocation data, audio, electronic, visual or similar information, and inferences drawn from the above.
* The sources of personal information from whom we collected are: directly from you, automatically or from third parties.
* The business or commercial purposes of collecting personal information are as summarized above and in our Privacy Statement under Processing Purposes.
* We disclosed the following categories of personal information for a business purpose in the last 12 months: identifiers/contact information, demographic information (such as gender and rough geographic location), payment information, commercial information, Internet or other electronic network activity information, geolocation data, audio, electronic, visual or similar information, and inferences drawn from the above. We disclosed each category to third-party business partners and service providers, third-party sites or platforms such as social networking sites, and other third parties as described in the Sharing of Personal Data section of our Privacy Statement.
* As defined by applicable law, we “shared” the following categories of personal information in the last 12 months: identifiers/contact information, Internet or other electronic network activity information, and inferences drawn from the above. We shared each category to or with advertising networks, data analytics providers, and social networks.
* The business or commercial purpose of sharing personal information is to assist us with marketing, advertising, and audience measurement.
* We do not “sell” or “share” the personal information of known minors under 16 years of age.

#### Shine the Light Act

Under California Civil Code section 1798.83, also known as the “Shine the Light” law, California residents who have provided personal information to a business with which the individual has established a business relationship for personal, family, or household purposes (“California Customers”) may request information about whether the business has disclosed personal information to any third parties for the third parties’ direct marketing purposes. Please be aware that we do not disclose personal information to any third parties for their direct marketing purposes as defined by this law. California Customers may request further information about our compliance with this law by emailing (privacy\[at]github\[dot]com). Please note that businesses are required to respond to one request per California Customer each year and may not be required to respond to requests made by means other than through the designated email address.

#### Removal of Content

California residents under the age of 18 who are registered users of online sites, services, or applications have a right under California Business and Professions Code Section 22581 to remove, or request and obtain removal of, content or information they have publicly posted. To remove content or information you have publicly posted, please submit a [Private Information Removal request](https://support.github.com/contact/private-information). Alternatively, to request that we remove such content or information, please send a detailed description of the specific content or information you wish to have removed to [GitHub support](https://support.github.com/request). Please be aware that your request does not guarantee complete or comprehensive removal of content or information posted online and that the law may not permit or require removal in certain circumstances. If you have any questions about our privacy practices with respect to California residents, please send an email to privacy\[at]github\[dot]com.

We value the trust you place in us and are committed to handling your personal information with care and respect. If you have any questions or concerns about our privacy practices, please email our Data Protection Officer at dpo\[at]github\[dot]com.

### Colorado/Connecticut/Virginia

If you live in Colorado, Connecticut, or Virginia you have some additional rights:

* If we deny your rights request, you have the right to appeal that decision. We will provide you with the necessary information to submit an appeal at that time.
* You have the right to opt out of profiling in furtherance of decisions that produce legal or similarly significant effects concerning the consumer. GitHub does not engage in such profiling as defined by Colorado law, so there’s no need to opt out.

### Nevada

We do not sell your covered information, as defined under Chapter 603A of the Nevada Revised Statutes. If you still have questions about your covered information or anything else in our Privacy Statement, please send an email to privacy\[at]github\[dot]com.# Best practices for GitHub Copilot CLI

Learn how to get the most out of GitHub Copilot CLI.

## Introduction

GitHub Copilot CLI is a terminal-native AI coding assistant that brings agentic capabilities directly to your command line. Copilot CLI can operate like a chatbot, answering your questions, but its true power lies in its ability to work autonomously as your coding partner, allowing you to delegate tasks and oversee its work.

This article provides tips for getting the most out of Copilot CLI, from using the various CLI commands effectively to managing the CLI's access to files. Consider these tips as starting points, then experiment to find out what works best for your workflows.

> \[!NOTE]
> GitHub Copilot CLI is continually evolving. Use the `/help` command to see the most up to date information.

## 1. Customize your environment

### Use custom instructions files

Copilot CLI automatically reads instructions from multiple locations, allowing you to define organization-wide standards and repository-specific conventions.

**Supported locations (in order of discovery):**

| Location                                    | Scope                 |
| ------------------------------------------- | --------------------- |
| `~/.copilot/copilot-instructions.md`        | All sessions (global) |
| `.github/copilot-instructions.md`           | Repository            |
| `.github/instructions/**/*.instructions.md` | Repository (modular)  |
| `AGENTS.md` (in Git root or cwd)            | Repository            |
| `Copilot.md`, `GEMINI.md`, `CODEX.md`       | Repository            |

#### Best practice

Repository instructions **always take precedence** over global instructions. Use this to enforce team conventions. For example, this is a simple `.github/copilot-instructions.md` file.

```markdown
## Build Commands
- `npm run build` - Build the project
- `npm run test` - Run all tests
- `npm run lint:fix` - Fix linting issues

## Code Style
- Use TypeScript strict mode
- Prefer functional components over class components
- Always add JSDoc comments for public APIs

## Workflow
- Run `npm run lint:fix && npm test` after making changes
- Commit messages follow conventional commits format
- Create feature branches from `main`
```

> \[!TIP]
> Keep instructions concise and actionable. Lengthy instructions can dilute effectiveness.

For more information, see [About customizing GitHub Copilot responses](/en/copilot/concepts/prompting/response-customization?tool=webui).

### Configure allowed tools

Manage which tools Copilot can run without asking for permission. When Copilot requests permission for an action, you can typically choose either to allow it just this time, or allow the tool to be used for the rest of the CLI session.

To reset previously approved tools, use:

```copilot
/reset-allowed-tools
```

You can also preconfigure allowed tools via CLI flags:

```bash
copilot --allow-tool='shell(git:*)' --deny-tool='shell(git push)'
```

**Common permission patterns:**

* `shell(git:*)` — Allow all Git commands
* `shell(npm run:*)` — Allow all npm scripts
* `shell(npm run test:*)` — Allow npm test commands
* `write` — Allow file writes

### Select your preferred model

Use `/model` to choose from available models based on your task complexity:

| Model                         | Best For                                                       | Tradeoffs                                                                                                      |
| ----------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Claude Opus 4.5** (default) | Complex architecture, difficult debugging, nuanced refactoring | Most capable but uses more [premium requests](/en/copilot/concepts/billing/copilot-requests#model-multipliers) |
| **Claude Sonnet 4.5**         | Day-to-day coding, most routine tasks                          | Fast, cost-effective, handles most work well                                                                   |
| **GPT-5.2 Codex**             | Code generation, code review, straightforward implementations  | Excellent for reviewing code produced by other models                                                          |

**Recommendations:**

* **Opus 4.5** is ideal for tasks requiring deep reasoning, complex system design, subtle bug investigation, or extensive context understanding.
* **Switch to Sonnet 4.5** for routine tasks where speed and cost efficiency matter—it handles the majority of everyday coding effectively.
* **Use Codex** for high-volume code generation and as a second opinion for reviewing code produced by other models.

You can switch models mid-session with `/model` as task complexity changes.

## 2. Plan before you code

### Plan mode

**Models achieve higher success rates when given a concrete plan to follow.** In plan mode, Copilot will create a structured implementation plan before any code is written.

Press <kbd>Shift</kbd>+<kbd>Tab</kbd> to toggle between normal mode and plan mode. In plan mode, all prompts you enter will trigger the plan workflow.

Alternatively, you can use  the `/plan` command in normal mode to achieve the same effect.

**Example prompt (from normal mode):**

```copilot
/plan Add OAuth2 authentication with Google and GitHub providers
```

**What happens:**

* Copilot analyzes your request and codebase.
* **Asks clarifying questions** to align on requirements and approach.
* Creates a structured implementation plan with checkboxes.
* Saves the plan to `plan.md` in your session folder.
* **Waits for your approval** before implementing.

You can press <kbd>Ctrl</kbd>+<kbd>y</kbd> to view and edit the plan in your default editor for Markdown files.

**Example plan output:**

```markdown
# Implementation Plan: OAuth2 Authentication

## Overview
Add social authentication using OAuth2 with Google and GitHub providers.

## Tasks
- [ ] Install dependencies (passport, passport-google-oauth20, passport-github2)
- [ ] Create authentication routes in `/api/auth`
- [ ] Implement passport strategies for each provider
- [ ] Add session management middleware
- [ ] Create login/logout UI components
- [ ] Add environment variables for OAuth credentials
- [ ] Write integration tests

## Detailed Steps
1. **Dependencies**: Add to package.json...
2. **Routes**: Create `/api/auth/google` and `/api/auth/github`...
```

### When to use plan mode

| Scenario                           | Use plan mode?                                                                                                                                                                                                                                                                                                                                                                                                           |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Complex multi-file changes         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                       |
| Refactoring with many touch points | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                       |
| New feature implementation         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                       |
| Quick bug fixes                    | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |
| Single file changes                | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |

### The explore → plan → code → commit workflow

For best results on complex tasks:

* **Explore**:

  `Read the authentication files but don't write code yet`

* **Plan**:

  `/plan Implement password reset flow`

* **Review**:

  Check the plan, suggest modifications

* **Implement**:

  `Proceed with the plan`

* **Verify**:

  `Run the tests and fix any failures`

* **Commit**:

  `Commit these changes with a descriptive message`

## 3. Leverage infinite sessions

### Automatic context window management

Copilot CLI features **infinite sessions**. You don't need to worry about running out of context. The system automatically manages context through intelligent compaction that summarizes conversation history while preserving essential information.

**Session storage location:**

```text
~/.copilot/session-state/{session-id}/
├── events.jsonl      # Full session history
├── workspace.yaml    # Metadata
├── plan.md           # Implementation plan (if created)
├── checkpoints/      # Compaction history
└── files/            # Persistent artifacts
```

> \[!NOTE]
> If you ever need to manually trigger compaction, use `/compact`. This is rarely necessary since the system handles it automatically.

### Session management commands

To view information about the current CLI session, enter:

```copilot
/session
```

To view a list of any session checkpoints, enter:

```copilot
/session checkpoints
```

> \[!NOTE]
> A checkpoint is created when session context is compacted, and allows you to view the summary context that Copilot created.

To view the details of a specific checkpoint, enter:

```copilot
/session checkpoints NUMBER
```

where NUMBER specifies the checkpoint you want to display.

To view any temporary files that have been created during the current session—for example, artifacts created by Copilot that shouldn't be saved to the repository—enter:

```copilot
/session files
```

To view the current plan (if Copilot has generated one), enter:

```copilot
/session plan
```

### Best practice: Keep sessions focused

While infinite sessions allow long-running work, focused sessions produce better results:

* Use `/clear` or `/new` between unrelated tasks.
* This resets context and improves response quality.
* Think of it like starting a fresh conversation with a colleague.

### The `/context` command

Visualize your current context usage with `/context`. It shows a breakdown of:

* System/tools tokens
* Message history tokens
* Available free space
* Buffer allocation

## 4. Delegate work effectively

### The `/delegate` command

**Offload work to run in the cloud using Copilot coding agent.** This is particularly powerful for:

* Tasks that can run asynchronously.
* Changes to other repositories.
* Long-running operations you don't want to wait for.

**Example prompt:**

```copilot
/delegate Add dark mode support to the settings page
```

**What happens:**

* Your request is sent to Copilot coding agent.
* The agent creates a pull request with the changes.
* You can continue working locally while the cloud agent works.

### When to use `/delegate`

| Use `/delegate`              | Work locally            |
| ---------------------------- | ----------------------- |
| Tangential tasks             | Core feature work       |
| Documentation updates        | Debugging               |
| Refactoring separate modules | Interactive exploration |

## 5. Common workflows

### Codebase onboarding

Use Copilot CLI as your pair programming partner when joining a new project. For example, you could ask Copilot:

* `How is logging configured in this project?`
* `What's the pattern for adding a new API endpoint?`
* `Explain the authentication flow`
* `Where are the database migrations?`

### Test-driven development

Pair with Copilot CLI to develop tests.

* `Write failing tests for the user registration flow`
* *Review and approve the tests.*
* `Now implement code to make all tests pass`
* *Review the implementation.*
* `Commit with message "feat: add user registration"`

### Code review assistance

* ``/review Use Opus 4.5 and Codex 5.2 to review the changes in my current branch against `main`. Focus on potential bugs and security issues.``

### Git operations

Copilot excels at Git workflows:

* ``What changes went into version `2.3.0`?``
* `Create a PR for this branch with a detailed description`
* ``Rebase this branch against `main` ``
* ``Resolve the merge conflicts in `package.json` ``

### Bug investigation

* ``The `/api/users` endpoint returns 500 errors intermittently. Search the codebase and logs to identify the root cause.``

### Refactoring

* `/plan Migrate all class components to functional components with hooks`

  Then answer the questions Copilot asks. Review the plan it creates, and ask Copilot to make changes if necessary. When you are happy with the plan you can prompt:
  `Implement this plan`

## 6. Advanced patterns

### Work across multiple repositories

**Copilot CLI provides flexible multi-repository workflows**—a key differentiator for teams working on microservices, monorepos, or related projects.

**Option 1: Run from a parent directory**

```bash
# Navigate to a parent directory containing multiple repos
cd ~/projects
copilot
```

Copilot can now access and work across all child repositories simultaneously. This is ideal for:

* Microservices architectures
* Making coordinated changes across related repos
* Refactoring shared patterns across projects

**Option 2: Use `/add-dir` to expand access**

```bash
# Start in one repo, then add others (requires full paths)
copilot
/add-dir /Users/me/projects/backend-service
/add-dir /Users/me/projects/shared-libs
/add-dir /Users/me/projects/documentation
```

**View and manage allowed directories:**

```copilot
/list-dirs
```

**Example workflow: coordinated API changes**

```copilot
I need to update the user authentication API. The changes span:

- @/Users/me/projects/api-gateway (routing changes)
- @/Users/me/projects/auth-service (core logic)
- @/Users/me/projects/frontend (client updates)

Start by showing me the current auth flow across all three repos.
```

This multi-repository capability enables:

* Cross-cutting refactors (update a shared pattern everywhere)
* API contract changes with client updates
* Documentation that references multiple codebases
* Dependency upgrades across a monorepo

### Using images for UI work

Copilot can work with visual references. Simply **drag and drop** images directly into the CLI input, or reference image files:

```copilot
Implement this design: @mockup.png
Match the layout and spacing exactly
```

### Checklists for complex migrations

For large-scale changes:

```copilot
Run the linter and write all errors to `migration-checklist.md` as a checklist.
Then fix each issue one by one, checking them off as you go.
```

### Autonomous task completion

Switch into autopilot mode to allow Copilot to work autonomously on a task until it is complete. This is ideal for long-running tasks that don't require constant supervision. For more information, see [Allowing GitHub Copilot CLI to work autonomously](/en/copilot/concepts/agents/copilot-cli/autopilot).

Optionally, you can usually speed up large tasks by using the `/fleet` slash command at the start of your prompt to allow Copilot to break the task into parallel subtasks that are run by subagents. For more information, see [Running tasks in parallel with the \`/fleet\` command](/en/copilot/concepts/agents/copilot-cli/fleet).

## 7. Team guidelines

### Recommended repository setup

* **Create `.github/copilot-instructions.md`** with:
  * Build and test commands
  * Code style guidelines
  * Required checks before commits
  * Architecture decisions

* **Establish conventions** for:
  * When to use `/plan` (complex features, refactoring)
  * When to use `/delegate` (tangential work)
  * Code review processes with AI assistance

### Security considerations

* Copilot CLI requires explicit approval for potentially destructive operations.
* Review all proposed changes before accepting.
* Use permission allowlists judiciously.
* Never commit secrets. Copilot is designed to avoid this, but always verify.

### Measuring productivity

Track metrics like:

* Time from issue to pull request
* Number of iterations before merge
* Code review feedback cycles
* Test coverage improvements

## Getting help

From the command line, you can display help by using the command: `copilot -h`.

For help on various topics enter:

```bash
copilot help TOPIC
```

where `TOPIC` can be one of: `config`, `commands`, `environment`, `logging`, or `permissions`.

### Within the CLI

For help within the CLI, enter:

```copilot
/help
```

To view usage statistics, enter:

```copilot
/usage
```

To submit private feedback to GitHub about Copilot CLI, raise a bug report, or submit a feature request, enter:

```copilot
/feedback
```

## Hands-on practice

Try the [Creating applications with Copilot CLI](https://github.com/skills/create-applications-with-the-copilot-cli) Skills exercise for practical experience building an application with Copilot CLI.

Here is what you will learn:

* Install Copilot CLI
* Use the issue template to create an issue
* Generate a Node.js CLI calculator app
* Expand calculator functionality
* Write unit tests for calculator functions
* Create, review, and merge your pull request

## Further reading

* [About GitHub Copilot CLI](/en/copilot/concepts/agents/about-copilot-cli)
* [Using GitHub Copilot CLI](/en/copilot/how-tos/use-copilot-agents/use-copilot-cli)
* [GitHub Copilot CLI command reference](/en/copilot/reference/copilot-cli-reference/cli-command-reference)
* [Copilot plans and pricing](https://github.com/features/copilot/plans)# Allowing GitHub Copilot CLI to work autonomously

The CLI's autopilot mode lets Copilot CLI work autonomously on a task, carrying out multiple steps until the task is complete.

## Overview

Typically, when you use Copilot CLI interactively, you submit a prompt and then wait for Copilot CLI to respond before giving the next instruction. This back-and-forth interaction continues until the task is done.

Autopilot mode allows Copilot CLI to work through a task without waiting for your input after each step. Once you give the initial instruction, Copilot CLI works through each step autonomously until it determines the task is complete.

The difference between the CLI's standard interactive mode and autopilot mode is like the difference between working on a task with a coworker, where they do most of the work, but check back with you periodically, versus handing the task over to your colleague, saying "Here's what I need—let me know when you're finished."

In autopilot mode, Copilot keeps on going until one of these happens:

* The agent determines that the task is complete.
* A problem occurs that prevents further progress.
* You press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the agent from continuing.
* The maximum continuation limit is reached (if set).

To switch into autopilot mode during an interactive session, press <kbd>Shift</kbd>+<kbd>Tab</kbd> and cycle through the available modes until you reach autopilot mode, then enter your prompt. Use the same keypress to switch from autopilot mode back to the standard interactive mode.

## Benefits of autopilot mode

* **Hands-off automation:** Copilot completes tasks without needing your input after the initial instruction.
* **Efficiency:** Ideal for well-defined tasks like writing tests, refactoring files, or fixing CI failures. Autopilot is particularly suited for large tasks that require long-running, multi-step sessions.
* **Batch operations:** Useful for scripting and CI workflows where you want Copilot to run to completion.
* **Safety:** Autopilot mode allows Copilot to take multiple self-directed steps to finish your task. `--max-autopilot-continues` limits how many steps it can take before stopping, to avoid infinite loops. Also, in autopilot mode, Copilot cannot carry out any actions that require permission unless you explicitly grant it full permissions.

## Things to consider

* **Task suitability:** Autopilot mode is best for well-defined tasks. It is not ideal for open-ended exploration, feature development without a clear goal, or tasks where you want to guide the ongoing work.

  Copilot will do its best to complete any task, but it may struggle with vague or ambiguous instructions or tasks that require nuanced judgment calls along the way. This may result in a set of code changes that aren't what you expected and can't be used without remedial work.

* **Trust:** You need to trust Copilot to make reasonable decisions. Autopilot mode works best when you grant it approval for all permissions. This is equivalent to running Copilot CLI with the `--allow-all` option. You should be aware that this gives the CLI permission to make any changes it deems necessary to complete the task, including altering and deleting files.

* **Cost:** Autopilot mode uses premium requests in the same way that these are used when you are working in the standard interactive interface. In the standard mode, one premium request is used when you submit your initial prompt, and then an additional premium request is used each time you reply to a question in the CLI and the agent uses your response to interact with the AI model. The same applies in autopilot mode, except that you are not involved in initiating the next step, so the use of additional premium requests happens without your direct involvement.

  The billable premium request usage is determined using a multiplier. The multiplier varies depending on which model you use. Use the `/model` slash command to see the currently selected model and its multiplier, and change the model if required. For more information, see [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests) and [About billing for individual GitHub Copilot plans](/en/copilot/concepts/billing/billing-for-individuals#about-premium-requests).

  Each time the agent continues autonomously it will display a message in the CLI telling you how many premium requests have been used by that continuation step—taking account of the model multiplier—for example: `Continuing autonomously (3 premium requests)`.

## Permissions

When entering autopilot mode, if you have not already granted Copilot all permissions, a message is displayed prompting you to choose between three options:

```text
1. Enable all permissions (recommended)
2. Continue with limited permissions
3. Cancel (Esc)
```

You will get the best results from autopilot mode if you enable all permissions. If you choose to continue with limited permissions, Copilot will automatically deny any tool requests that require approval, which may prevent it from completing certain tasks. You can change your mind later and grant full permissions, during an autopilot session, by using the `/allow-all` command (or its alias `/yolo`).

## Comparing autopilot mode, `--allow-all`, and `--no-ask-user`

`--allow-all`, and its alias `--yolo`, are permissions-related options that you can pass to the `copilot` command when you start an interactive session. For a full list of available options, see [GitHub Copilot CLI command reference](/en/copilot/reference/copilot-cli-reference/cli-command-reference#command-line-options).

The `--allow-all` and `--yolo` options allow the CLI agent to use all tools, paths, and URLs. You can also set these permissions during an interactive session, by using the `/allow-all` or `/yolo` slash commands.

> \[!NOTE]
> Entering `/allow-all` and `/yolo` enables permissions for the current session. Entering these slash commands again does not disable permissions—in other words, these commands don't toggle permissions on and off.

With `--allow-all`, you are still in the normal interactive flow. Copilot will still stop and ask you what you want it to do when it reaches a decision point. However, when Copilot CLI needs to do something that would normally require approval, such as using tools, paths, or URLs, it will go ahead without asking for permission.

The `--no-ask-user` option suppresses clarifying questions that Copilot would normally ask. Instead the agent must make decisions on its own, rather than asking for your input. This provides a degree of autonomy. However, unlike autopilot mode, `--no-ask-user` does not allow the agent to continue working on a task through successive steps where interaction with the AI model is required. With this option, the CLI won't use additional premium requests, after your initial prompt, without your involvement.

## Typical workflow for using autopilot mode

Autopilot mode is ideal for implementing a large, detailed plan of work. Often you will find it useful to switch to autopilot mode after working with Copilot in plan mode to create an implementation plan. For more information about plan mode, see [Best practices for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/cli-best-practices#2-plan-before-you-code).

For example:

* Start an interactive Copilot CLI session.

  Optionally, you can include the `--allow-all` option to grant permissions, and the `--max-autopilot-continues` option to set a maximum continuation limit for autopilot mode during the session. For example, you could start the session with `copilot --allow-all --max-autopilot-continues 10` to give the agent permission to use all tools, paths, and URLs, and set a maximum continuation limit for autopilot to 10.

* When the interactive session starts, if you're prompted to trust the files in the current folder, accept this option.

* Press <kbd>Shift</kbd>+<kbd>Tab</kbd> to switch to plan mode, enter a prompt describing what you want to achieve, then work with Copilot to create a detailed plan.

* Once you have a plan that you are happy with, use the option that the CLI presents to "Accept plan and build on autopilot".

* If you're prompted about permissions, choose the option to enable all permissions.

* Leave Copilot to implement the plan. You can check in on its progress periodically.

## Using autopilot mode programmatically

You can use autopilot mode when you run Copilot CLI programmatically, for example when you pass Copilot a prompt on the command line, or when you use the CLI as part of a script or CI workflow. Doing so allows you to automate tasks end-to-end without needing to interact with the CLI after the initial command.

Use the `--allow-all` (or `--yolo`) option to grant Copilot permission to use all tools, paths, and URLs. You can include the `--max-autopilot-continues` option to set a maximum continuation limit to prevent runaway loops. This is especially important in programmatic contexts where you won't be there to intervene if something goes wrong.

Example usage:

```shell
copilot --autopilot --yolo --max-autopilot-continues 10 -p "YOUR PROMPT HERE"
```

## Summary

Use autopilot mode when you want Copilot to take over a task and work to completion without your involvement. It's best for clear, well-defined tasks where you trust Copilot to make reasonable decisions.

## Further reading

* [Using GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/use-copilot-cli#get-copilot-to-work-autonomously)
* [Running tasks in parallel with the \`/fleet\` command](/en/copilot/concepts/agents/copilot-cli/fleet)
* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)# Allowing GitHub Copilot CLI to work autonomously

The CLI's autopilot mode lets Copilot CLI work autonomously on a task, carrying out multiple steps until the task is complete.

## Overview

Typically, when you use Copilot CLI interactively, you submit a prompt and then wait for Copilot CLI to respond before giving the next instruction. This back-and-forth interaction continues until the task is done.

Autopilot mode allows Copilot CLI to work through a task without waiting for your input after each step. Once you give the initial instruction, Copilot CLI works through each step autonomously until it determines the task is complete.

The difference between the CLI's standard interactive mode and autopilot mode is like the difference between working on a task with a coworker, where they do most of the work, but check back with you periodically, versus handing the task over to your colleague, saying "Here's what I need—let me know when you're finished."

In autopilot mode, Copilot keeps on going until one of these happens:

* The agent determines that the task is complete.
* A problem occurs that prevents further progress.
* You press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the agent from continuing.
* The maximum continuation limit is reached (if set).

To switch into autopilot mode during an interactive session, press <kbd>Shift</kbd>+<kbd>Tab</kbd> and cycle through the available modes until you reach autopilot mode, then enter your prompt. Use the same keypress to switch from autopilot mode back to the standard interactive mode.

## Benefits of autopilot mode

* **Hands-off automation:** Copilot completes tasks without needing your input after the initial instruction.
* **Efficiency:** Ideal for well-defined tasks like writing tests, refactoring files, or fixing CI failures. Autopilot is particularly suited for large tasks that require long-running, multi-step sessions.
* **Batch operations:** Useful for scripting and CI workflows where you want Copilot to run to completion.
* **Safety:** Autopilot mode allows Copilot to take multiple self-directed steps to finish your task. `--max-autopilot-continues` limits how many steps it can take before stopping, to avoid infinite loops. Also, in autopilot mode, Copilot cannot carry out any actions that require permission unless you explicitly grant it full permissions.

## Things to consider

* **Task suitability:** Autopilot mode is best for well-defined tasks. It is not ideal for open-ended exploration, feature development without a clear goal, or tasks where you want to guide the ongoing work.

  Copilot will do its best to complete any task, but it may struggle with vague or ambiguous instructions or tasks that require nuanced judgment calls along the way. This may result in a set of code changes that aren't what you expected and can't be used without remedial work.

* **Trust:** You need to trust Copilot to make reasonable decisions. Autopilot mode works best when you grant it approval for all permissions. This is equivalent to running Copilot CLI with the `--allow-all` option. You should be aware that this gives the CLI permission to make any changes it deems necessary to complete the task, including altering and deleting files.

* **Cost:** Autopilot mode uses premium requests in the same way that these are used when you are working in the standard interactive interface. In the standard mode, one premium request is used when you submit your initial prompt, and then an additional premium request is used each time you reply to a question in the CLI and the agent uses your response to interact with the AI model. The same applies in autopilot mode, except that you are not involved in initiating the next step, so the use of additional premium requests happens without your direct involvement.

  The billable premium request usage is determined using a multiplier. The multiplier varies depending on which model you use. Use the `/model` slash command to see the currently selected model and its multiplier, and change the model if required. For more information, see [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests) and [About billing for individual GitHub Copilot plans](/en/copilot/concepts/billing/billing-for-individuals#about-premium-requests).

  Each time the agent continues autonomously it will display a message in the CLI telling you how many premium requests have been used by that continuation step—taking account of the model multiplier—for example: `Continuing autonomously (3 premium requests)`.

## Permissions

When entering autopilot mode, if you have not already granted Copilot all permissions, a message is displayed prompting you to choose between three options:

```text
1. Enable all permissions (recommended)
2. Continue with limited permissions
3. Cancel (Esc)
```

You will get the best results from autopilot mode if you enable all permissions. If you choose to continue with limited permissions, Copilot will automatically deny any tool requests that require approval, which may prevent it from completing certain tasks. You can change your mind later and grant full permissions, during an autopilot session, by using the `/allow-all` command (or its alias `/yolo`).

## Comparing autopilot mode, `--allow-all`, and `--no-ask-user`

`--allow-all`, and its alias `--yolo`, are permissions-related options that you can pass to the `copilot` command when you start an interactive session. For a full list of available options, see [GitHub Copilot CLI command reference](/en/copilot/reference/copilot-cli-reference/cli-command-reference#command-line-options).

The `--allow-all` and `--yolo` options allow the CLI agent to use all tools, paths, and URLs. You can also set these permissions during an interactive session, by using the `/allow-all` or `/yolo` slash commands.

> \[!NOTE]
> Entering `/allow-all` and `/yolo` enables permissions for the current session. Entering these slash commands again does not disable permissions—in other words, these commands don't toggle permissions on and off.

With `--allow-all`, you are still in the normal interactive flow. Copilot will still stop and ask you what you want it to do when it reaches a decision point. However, when Copilot CLI needs to do something that would normally require approval, such as using tools, paths, or URLs, it will go ahead without asking for permission.

The `--no-ask-user` option suppresses clarifying questions that Copilot would normally ask. Instead the agent must make decisions on its own, rather than asking for your input. This provides a degree of autonomy. However, unlike autopilot mode, `--no-ask-user` does not allow the agent to continue working on a task through successive steps where interaction with the AI model is required. With this option, the CLI won't use additional premium requests, after your initial prompt, without your involvement.

## Typical workflow for using autopilot mode

Autopilot mode is ideal for implementing a large, detailed plan of work. Often you will find it useful to switch to autopilot mode after working with Copilot in plan mode to create an implementation plan. For more information about plan mode, see [Best practices for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/cli-best-practices#2-plan-before-you-code).

For example:

* Start an interactive Copilot CLI session.

  Optionally, you can include the `--allow-all` option to grant permissions, and the `--max-autopilot-continues` option to set a maximum continuation limit for autopilot mode during the session. For example, you could start the session with `copilot --allow-all --max-autopilot-continues 10` to give the agent permission to use all tools, paths, and URLs, and set a maximum continuation limit for autopilot to 10.

* When the interactive session starts, if you're prompted to trust the files in the current folder, accept this option.

* Press <kbd>Shift</kbd>+<kbd>Tab</kbd> to switch to plan mode, enter a prompt describing what you want to achieve, then work with Copilot to create a detailed plan.

* Once you have a plan that you are happy with, use the option that the CLI presents to "Accept plan and build on autopilot".

* If you're prompted about permissions, choose the option to enable all permissions.

* Leave Copilot to implement the plan. You can check in on its progress periodically.

## Using autopilot mode programmatically

You can use autopilot mode when you run Copilot CLI programmatically, for example when you pass Copilot a prompt on the command line, or when you use the CLI as part of a script or CI workflow. Doing so allows you to automate tasks end-to-end without needing to interact with the CLI after the initial command.

Use the `--allow-all` (or `--yolo`) option to grant Copilot permission to use all tools, paths, and URLs. You can include the `--max-autopilot-continues` option to set a maximum continuation limit to prevent runaway loops. This is especially important in programmatic contexts where you won't be there to intervene if something goes wrong.

Example usage:

```shell
copilot --autopilot --yolo --max-autopilot-continues 10 -p "YOUR PROMPT HERE"
```

## Summary

Use autopilot mode when you want Copilot to take over a task and work to completion without your involvement. It's best for clear, well-defined tasks where you trust Copilot to make reasonable decisions.

## Further reading

* [Using GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/use-copilot-cli#get-copilot-to-work-autonomously)
* [Running tasks in parallel with the \`/fleet\` command](/en/copilot/concepts/agents/copilot-cli/fleet)
* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)# Running tasks in parallel with the `/fleet` command

The /fleet slash command lets Copilot CLI break down a complex request into smaller tasks and run them in parallel, maximizing efficiency and throughput.

## Introduction

The `/fleet` slash command in Copilot CLI is designed to take an implementation plan and break it down into smaller, independent tasks that can be executed in parallel by subagents. This allows for faster completion of complex requests that involve multiple steps.

This article gives an overview of the `/fleet` slash command. For details of how to use it, see [Speeding up task completion with the \`/fleet\` command](/en/copilot/how-tos/copilot-cli/speeding-up-task-completion).

## How `/fleet` works

When you use the `/fleet` command, the main Copilot agent analyzes the prompt and determines whether it can be divided into smaller subtasks. It will assess, based on the nature of the subtasks and their dependencies, whether these can be efficiently executed by subagents. If it decides to assign some or all of the subtasks to subagents, it will act as orchestrator, managing the workflow and dependencies between the subtasks. Where possible, the orchestrator agent will run the subagents in parallel, allowing the whole task to be completed more quickly.

## Benefits of using `/fleet`

* **Speed of task completion**: The main benefit of using the `/fleet` command is that a large, multi-part task can be completed more quickly by running subtasks in parallel. Whether parts of a large task can be worked on in parallel will be determined by the dependencies between the subtasks. Some tasks, such as creating a suite of tests for a new feature, are well suited to parallelization and will typically complete faster when you use the `/fleet` slash command.

* **Specialization**: If you've defined custom agents that are specialized for certain types of work, these may be used by the subagents. This allows for specialization, with the subagents using the custom agents best suited to the specific subtask they are working on.

  By default, subagents use a low-cost AI model. However, you can tell Copilot to use a specific model for part of the work. For example, within a larger prompt, you could specify `... Use GPT-5.3-Codex, to create ... Use Claude Opus 4.5, to analyze ...`. If a subagent uses a custom agent profile that specifies a particular AI model, then that model will be used by the subagent. Using a specific model may produce better quality results for particular types of subtask.

  If custom agents are available, Copilot will decide whether to use one to complete a particular subtask. However, if you know that a specific custom agent is well-suited to a particular subtask, you can specify this in your prompt by using `@CUSTOM-AGENT-NAME`. For example, within a larger prompt: `... Use @test-writer to create comprehensive unit tests for ...`.

  For more information, see [Creating and using custom agents for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli).

* **Context window**: Each subagent has its own context window, separate from the main agent and other subagents. This allows each subagent to focus on its specific task without being overwhelmed by the full context of the larger task.

## When should you use `/fleet`?

* **Large or complex tasks**: When your request involves multiple independent steps, such as refactoring several files, updating dependencies, or running tests across modules.
* **Parallelizable work**: If your task can be split into subtasks that don’t depend on each other.
* **Automated workflows**: When you want the quickest possible completion of a large task—for example, when you're using autopilot mode to allow Copilot to work autonomously.

## Points to consider

* **Premium request usage**: When you submit a prompt in the CLI and Copilot interacts with the selected large language model (LLM) to generate a response, this consumes premium requests. The number of premium requests consumed depends on the model that's currently selected. More interactions with the LLM result in more premium requests being consumed.

  Each subagent can interact with the LLM independently of the main agent, so splitting work up into smaller tasks that are run by subagents may result in more LLM interactions than if the work was handled by the main agent. Using `/fleet` in a prompt may therefore cause more premium requests to be consumed.

  The billable premium request usage is determined using a multiplier. The multiplier varies depending on which model you use. Use the `/model` slash command to see the currently selected model and its multiplier, and change the model if required. For more information, see [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests) and [About billing for individual GitHub Copilot plans](/en/copilot/concepts/billing/billing-for-individuals#about-premium-requests).

* **Task composition**: Work is best suited to execution by multiple subagents if it can be decomposed into independent subtasks. If your request is inherently sequential, using the `/fleet` slash command mode may not provide any benefit.

## Relationship between `/fleet` and autopilot mode

The `/fleet` slash command is often used in autopilot mode, but these are distinct features that can be used independently:

* **Autopilot mode** allows Copilot to continue working autonomously until a task is complete, auto-responding to requests that would otherwise require user intervention.
* **`/fleet`** is all about using subagents to execute tasks in parallel, while the main agent manages the overall workflow. You can use the `/fleet` slash command in interactive sessions independently of autopilot mode.

A typical workflow for using `/fleet` in autopilot mode might look like this:

1. Press <kbd>Shift</kbd>+<kbd>Tab</kbd> to switch into plan mode and work with Copilot CLI to create an implementation plan.
2. Recognize that the completed plan contains multiple elements and looks like a good candidate for `/fleet`.
3. Select the **Accept plan and build on autopilot + /fleet** option that's displayed when the plan is complete.

For more information about autopilot mode, see [Allowing GitHub Copilot CLI to work autonomously](/en/copilot/concepts/agents/copilot-cli/autopilot).

## Further reading

* [Speeding up task completion with the \`/fleet\` command](/en/copilot/how-tos/copilot-cli/speeding-up-task-completion)
* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)
* [Using GitHub Copilot CLI](/en/copilot/how-tos/use-copilot-agents/use-copilot-cli)# Acelerar la finalización de tareas con el comando `/fleet`

Aprende cómo puedes acelerar la finalización de un plan de implementación de varios pasos utilizando el comando /fleet slash.

Cuando una tarea implica varias operaciones, algunas o todas las cuales pueden realizarse en paralelo, el comando `/fleet` puede acelerar su finalización. Al usar este comando, Copilot asigna partes separadas del trabajo a subagentes.

Para obtener más información, consulte [Ejecución de tareas en paralelo con el comando `/fleet`](/en/copilot/concepts/agents/copilot-cli/fleet).

## Uso del comando de barra inclinada `/fleet`

Para usar el comando de barra `/fleet`, ingrese el comando seguido de su indicador.

### Flujo de trabajo típico

Normalmente, utilizarás el comando de barra inclinada `/fleet` después de crear un plan de implementación.

1. En una sesión interactiva de CLI, pulse <kbd>Shift</kbd>+<kbd>Tab</kbd> para cambiar al modo de planificación.
2. Introduzca una breve descripción de la función que desea agregar o del cambio que desea realizar.
3. Trabaje con Copilot en modo de planificación para crear un plan de implementación.
4. Una vez que el plan esté completo, seleccione una de las siguientes opciones:

   * **Acepte el plan y construya en piloto automático + /fleet** para permitir que Copilot utilice subagentes y trabaje de forma autónoma para implementar el plan sin ninguna otra entrada.
   * **Salga del modo de planificación y le pediré que continúe** y luego ingrese un comando como `/fleet implement the plan`. Copilot comenzará a trabajar en el plan, utilizando subagentes para ejecutar partes del trabajo en paralelo cuando sea posible. Es posible que le pida que responda preguntas o tome decisiones a medida que avanza en el plan.

### Seguimiento del progreso

Utilice el comando `/tasks` para ver una lista de las tareas en segundo plano relacionadas con la sesión actual. Esto incluirá cualquier subtarea gestionada por los subagentes cuando utilice el comando `/fleet`.

Utilice las teclas de flecha arriba y abajo del teclado para navegar por la lista de tareas en segundo plano. Para cada tarea de subagente, puede:

* Pulse <kbd>Enter</kbd> para ver los detalles. Cuando la subtarea esté completa, verá un resumen de lo que se ha hecho.
* Pulse <kbd>k</kbd> para finalizar el proceso.
* Pulse <kbd>r</kbd> para eliminar de la lista las subtareas completadas o canceladas.

Pulse <kbd>Esc</kbd> para salir de la lista de tareas y volver al indicador principal de la CLI.

## Lecturas adicionales

* [Referencia de comandos de la CLI de GitHub Copilot](/en/copilot/reference/copilot-cli-reference/cli-command-reference#slash-commands-in-the-interactive-interface)# Referencia de comandos de la CLI de GitHub Copilot

Encuentra comandos y atajos de teclado que te ayudarán a usar la interfaz de línea de comandos de Copilot de forma eficaz.

## Comandos de línea de comandos

| Comando | Propósito |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `copiloto` | Iniciar la interfaz de usuario interactiva. |
| `copilot help [tema]` | Muestra información de ayuda. Los temas de ayuda incluyen: `config`, `commands`, `environment`, `logging` y `permissions`. |
| `copilot init` | Inicializa las instrucciones personalizadas de Copilot para este repositorio. |
| `actualización de copiloto` | Descargue e instale la última versión. |
| `versión de copiloto` | Muestra la información de la versión y busca actualizaciones. |
| `copilot login` | Autentícate con Copilot a través del flujo de dispositivo OAuth. Acepta `--host HOST` para especificar la URL del host de GitHub (predeterminado: `https://github.com`). |
| `copilot logout` | Cierra sesión en GitHub y elimina las credenciales almacenadas. |
| `complemento copiloto` | Gestiona complementos y mercados de complementos. |

## Atajos globales en la interfaz interactiva

| Atajo | Propósito |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `@ NOMBRE_ARCHIVO` | Incluir el contenido del archivo en el contexto. |
| <kbd>Ctrl</kbd>+<kbd>X</kbd> luego `/` | Después de haber empezado a escribir un mensaje, esto le permite ejecutar un comando de barra diagonal; por ejemplo, si desea cambiar el modelo sin tener que volver a escribir el mensaje. |
| <kbd>Esc</kbd> | Cancelar la operación actual. |
| `! COMANDO` | Ejecuta un comando en tu shell local, omitiendo Copilot. |
| <kbd>Ctrl</kbd>+<kbd>C</kbd> | Cancelar operación / borrar entrada. Pulse dos veces para salir. |
| <kbd>Ctrl</kbd>+<kbd>D</kbd> | Apagar. |
| <kbd>Ctrl</kbd>+<kbd>L</kbd> | Borrar la pantalla. |
| <kbd>Shift</kbd>+<kbd>Tab</kbd> | Alterna entre el modo estándar, el modo plan y el modo piloto automático. |

## Atajos de línea de tiempo en la interfaz interactiva

| Atajo | Propósito |
| -------- | -------------------------------------------------------------------------------------------------------------------------- |
| ctrl+o | Aunque no haya nada en el campo de texto, esto expande los elementos recientes en la línea de tiempo de respuesta de Copilot para mostrar más detalles. |
| ctrl+e | Aunque no haya nada en el campo de texto, esto expande todos los elementos de la línea de tiempo de respuesta de Copilot. |
| Ctrl+T | Expandir/contraer la visualización del razonamiento en las respuestas. |

## Atajos de navegación en la interfaz interactiva

| Atajo | Propósito |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| <kbd>Ctrl</kbd>+<kbd>A</kbd> | Moverse al principio de la línea (al escribir). |
| <kbd>Ctrl</kbd>+<kbd>B</kbd> | Moverse al carácter anterior. |
| <kbd>Ctrl</kbd>+<kbd>E</kbd> | Moverse al final de la línea (al escribir). |
| <kbd>Ctrl</kbd>+<kbd>F</kbd> | Pasar al siguiente carácter. |
| <kbd>Ctrl</kbd>+<kbd>G</kbd> | Edite el mensaje en un editor externo. |
| <kbd>Ctrl</kbd>+<kbd>H</kbd> | Borra el carácter anterior. |
| <kbd>Ctrl</kbd>+<kbd>K</kbd> | Borra desde el cursor hasta el final de la línea. Si el cursor está al final de la línea, borra el salto de línea. |
| <kbd>Ctrl</kbd>+<kbd>U</kbd> | Borrar desde el cursor hasta el principio de la línea. |
| <kbd>Ctrl</kbd>+<kbd>W</kbd> | Borrar la palabra anterior. |
| <kbd>Inicio</kbd> | Ir al inicio de la línea actual. |
| <kbd>Fin</kbd> | Ir al final de la línea actual. |
| <kbd>Ctrl</kbd>+<kbd>Inicio</kbd> | Ir al inicio del texto. |
| <kbd>Ctrl</kbd>+<kbd>Fin</kbd> | Ir al final del texto. |
| <kbd>Meta</kbd>+<kbd>←</kbd>/<kbd>→</kbd> | Mueva el cursor una palabra. |
| <kbd>↑</kbd>/<kbd>↓</kbd> | Navegar por el historial de comandos. |

## Comandos de barra diagonal en la interfaz interactiva

| Comando | Propósito |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `/add-dir RUTA` | Agrega un directorio a la lista permitida para el acceso a archivos. |
| `/agente` | Explore y seleccione entre los agentes disponibles (si los hay). |
| `/allow-all`, `/yolo` | Habilita todos los permisos (herramientas, rutas y URL). |
| `/clear`, `/new` | Borrar el historial de la conversación. |
| `/compact` | Resume el historial de la conversación para reducir el uso de la ventana de contexto. |
| `/context` | Muestra el uso y la visualización de los tokens de la ventana de contexto. |
| `/cwd`, ​​`/cd [RUTA]` | Cambia el directorio de trabajo o muestra el directorio actual. |
| `/delegate [PROMPT]` | Delega los cambios a un repositorio remoto con una solicitud de extracción generada por IA. |
| `/diff` | Revisa los cambios realizados en el directorio actual. |
| `/exit`, `/quit` | Salir de la interfaz de línea de comandos. |
| `/experimental [on\|off]` | Activa o desactiva las funciones experimentales. |
| `/feedback` | Proporcione comentarios sobre la interfaz de línea de comandos (CLI). |
| `/fleet [PROMPT]` | Habilita la ejecución paralela de subagentes de partes de una tarea. Consulta [Ejecución de tareas en paralelo con el comando `/fleet`](/en/copilot/concepts/agents/copilot-cli/fleet). |
| `/help` | Muestra la ayuda para los comandos interactivos. |
| `/ide` | Conéctese a un espacio de trabajo IDE. |
| `/init` | Inicializa las instrucciones personalizadas de Copilot y las funciones de agente para este repositorio. |
| `/list-dirs` | Muestra todos los directorios para los que se ha permitido el acceso a archivos. |
| `/login` | Inicia sesión en Copilot. |
| `/logout` | Cerrar sesión en Copilot. |
| `/lsp [show\|test\|reload\|help] [SERVER-NAME]` | Gestiona la configuración del servidor de lenguaje. |
| `/mcp [show\|add\|edit\|delete\|disable\|enable] [SERVER-NAME]` | Administrar la configuración del servidor MCP. |
| `/model`, `/models [MODELO]` | Seleccione el modelo de IA que desea utilizar. |
| `/plan [PROMPT]` | Crea un plan de implementación antes de codificar. |
| `/plugin [marketplace\|install\|uninstall\|update\|list] [ARGS...]` | Gestiona plugins y mercados de plugins. |
| `/rename NOMBRE` | Cambiar el nombre de la sesión actual (alias para `/session rename`). |
| `/reset-allowed-tools` | Restablece la lista de herramientas permitidas. |
| `/resume [ID-DE-SESIÓN]` | Cambia a una sesión diferente eligiendo de una lista (opcionalmente, especifica un ID de sesión). |
| `/review [PROMPT]` | Ejecuta el agente de revisión de código para analizar los cambios. |
| `/session [checkpoints [n]\|files\|plan\|rename NAME]` | Muestra información de la sesión y un resumen del espacio de trabajo. Utilice los subcomandos para obtener más detalles. |
| `/share [archivo\|gist] [RUTA]` | Comparte la sesión en un archivo Markdown o en un gist de GitHub. |
| `/skills [list\|info\|add\|remove\|reload] [ARGS...]` | Gestiona las habilidades para obtener capacidades mejoradas. |
| `/terminal-setup` | Configure el terminal para admitir la entrada de varias líneas (<kbd>Shift</kbd>+<kbd>Enter</kbd> y <kbd>Ctrl</kbd>+<kbd>Enter</kbd>). |
| `/theme [show\|set\|list] [auto\|THEME-ID]` | Visualiza o configura el tema del terminal. |
| `/usage` | Muestra las métricas y estadísticas de uso de la sesión. |
| `/user [show\|list\|switch]` | Gestiona el usuario actual de GitHub. |

Para obtener una lista completa de los comandos de barra inclinada disponibles, escriba `/help` en la interfaz interactiva de la CLI.

## Opciones de línea de comandos

| Opción | Propósito |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--acp` | Iniciar el servidor del Protocolo de Cliente Agente. |
| `--add-dir=RUTA` | Agrega un directorio a la lista permitida para el acceso a archivos (puede usarse varias veces). |
| `--add-github-mcp-tool=TOOL` | Agrega una herramienta para habilitar en el servidor MCP de GitHub, en lugar del subconjunto CLI predeterminado (se puede usar varias veces). Usa `*` para todas las herramientas. |
| `--add-github-mcp-toolset=TOOLSET` | Agrega un conjunto de herramientas para habilitar en el servidor MCP de GitHub, en lugar del subconjunto CLI predeterminado (se puede usar varias veces). Usa `all` para todos los conjuntos de herramientas. |
| `--additional-mcp-config=JSON` | Agrega un servidor MCP solo para esta sesión. La configuración del servidor se puede proporcionar como una cadena JSON o una ruta de archivo (con el prefijo `@`). Complementa la configuración de `~/.copilot/mcp-config.json`. Sobrescribe cualquier configuración de servidor MCP instalada con el mismo nombre. |
| `--agent=AGENT` | Especifique un agente personalizado para usar. |
| `--allow-all` | Habilita todos los permisos (equivalente a `--allow-all-tools --allow-all-paths --allow-all-urls`). |
| `--allow-all-paths` | Deshabilita la verificación de la ruta del archivo y permite el acceso a cualquier ruta. |
| `--allow-all-tools` | Permite que todas las herramientas se ejecuten automáticamente sin confirmación. Requerido cuando se utiliza la CLI mediante programación (env: `COPILOT_ALLOW_ALL`). |
| `--allow-all-urls` | Permite el acceso a todas las URL sin confirmación. |
| `--allow-tool=TOOL ...` | Herramientas que la CLI tiene permiso para usar. No solicitará permiso. Para varias herramientas, utilice una lista entre comillas, separada por comas. |
| `--allow-url=URL ...` | Permite el acceso a URL o dominios específicos. Para varias URL, utilice una lista entre comillas, separada por comas. |
| `--alt-screen=VALOR` | Utiliza el búfer de pantalla alternativo del terminal (`on` o `off`). |
| `--autopilot` | Habilita la continuación del piloto automático en modo de solicitud. Consulta [Permitir que la CLI de GitHub Copilot funcione de forma autónoma](/en/copilot/concepts/agents/copilot-cli/autopilot). |
| `--available-tools=HERRAMIENTA ...` | Solo estas herramientas estarán disponibles para el modelo. Para varias herramientas, utilice una lista entre comillas, separada por comas. |
| `--banner` | Muestra el banner de inicio. |
| `--bash-env` | Habilita la compatibilidad con `BASH_ENV` para shells bash. |
| `--config-dir=RUTA` | Establece el directorio de configuración (predeterminado: `~/.copilot`). |
| `--continue` | Reanudar la sesión más reciente. |
| `--deny-tool=TOOL ...` | Herramientas que la CLI no tiene permiso para usar. No solicitará permiso. Para varias herramientas, utilice una lista entre comillas, separada por comas. |
| `--deny-url=URL ...` | Deniega el acceso a URL o dominios específicos; tiene prioridad sobre `--allow-url`. Para varias URL, utilice una lista entre comillas, separada por comas. |
| `--disable-builtin-mcps` | Deshabilita todos los servidores MCP integrados (actualmente: `github-mcp-server`). |
| `--disable-mcp-server=SERVER-NAME` | Deshabilita un servidor MCP específico (puede usarse varias veces). |
| `--disable-parallel-tools-execution` | Deshabilita la ejecución paralela de herramientas (LLM aún puede realizar llamadas a herramientas en paralelo, pero se ejecutarán secuencialmente). |
| `--disallow-temp-dir` | Impide el acceso automático al directorio temporal del sistema. |
| `--enable-all-github-mcp-tools` | Habilita todas las herramientas del servidor GitHub MCP, en lugar del subconjunto CLI predeterminado. Anula las opciones `--add-github-mcp-toolset` y `--add-github-mcp-tool`. |
| `--excluded-tools=HERRAMIENTA ...` | Estas herramientas no estarán disponibles para el modelo. Para varias herramientas, utilice una lista entre comillas, separada por comas. |
| `--experimental` | Habilitar funciones experimentales (use `--no-experimental` para deshabilitarlas). |
| `-h`, `--help` | Muestra la ayuda. |
| `-i PROMPT`, `--interactive=PROMPT` | Inicia una sesión interactiva y ejecuta automáticamente este mensaje. |
| `--log-dir=DIRECTORIO` | Establece el directorio del archivo de registro (predeterminado: `~/.copilot/logs/`). |
| `--log-level=NIVEL` | Establece el nivel de registro (opciones: `ninguno`, `error`, `advertencia`, `información`, `depuración`, `todos`, `predeterminado`). |
| `--max-autopilot-continues=COUNT` | Número máximo de mensajes de continuación en modo piloto automático (predeterminado: ilimitado). Consulte [Permitir que la CLI de GitHub Copilot funcione de forma autónoma](/en/copilot/concepts/agents/copilot-cli/autopilot). |
| `--model=MODELO` | Establece el modelo de IA que deseas utilizar. |
| `--no-alt-screen` | Deshabilita el búfer de pantalla alternativa del terminal. |
| `--no-ask-user` | Deshabilita la herramienta `ask_user` (el agente funciona de forma autónoma sin hacer preguntas). |
| `--no-auto-update` | Deshabilitar la descarga automática de actualizaciones de la CLI. |
| `--no-bash-env` | Deshabilitar la compatibilidad con `BASH_ENV` para shells bash. |
| `--no-color` | Desactivar toda la salida de color. |
| `--no-custom-instructions` | Deshabilita la carga de instrucciones personalizadas desde `AGENTS.md` y archivos relacionados. |
| `--no-experimental` | Deshabilitar las funciones experimentales. |
| `--output-format=FORMATO` | FORMATO puede ser `texto` (predeterminado) o `json` (genera JSONL: un objeto JSON por línea). |
| `-p PROMPT`, `--prompt=PROMPT` | Ejecuta un mensaje programáticamente (sale después de completarse). |
| `--plain-diff` | Deshabilita la representación enriquecida de diferencias (resaltado de sintaxis a través de la herramienta de diferencias especificada en tu configuración de Git). |
| `--resume=ID-DE-SESIÓN` | Reanuda una sesión interactiva anterior seleccionando un elemento de una lista (opcionalmente, especifique un ID de sesión). |
| `-s`, `--silent` | Muestra solo la respuesta del agente (sin estadísticas de uso), útil para scripts con `-p`. |
| `--screen-reader` | Habilitar las optimizaciones para lectores de pantalla. |
| `--secret-env-vars=VAR ...` | Una variable de entorno cuyo valor desea que se oculte en la salida. Para varias variables, utilice una lista entre comillas, separada por comas. Los valores de las variables de entorno `GITHUB_TOKEN` y `COPILOT_GITHUB_TOKEN` se ocultan de forma predeterminada. |
| `--share=RUTA` | Comparte una sesión en un archivo Markdown después de completar una sesión programática (ruta predeterminada: `./copilot-session-<ID>.md`). |
| `--share-gist` | Comparte una sesión en un gist secreto de GitHub después de completar una sesión programática. |
| `--stream=MODE` | Habilita o deshabilita el modo de transmisión (opciones de modo: `on` o `off`). |
| `-v`, `--version` | Mostrar información de la versión. |
| `--yolo` | Habilita todos los permisos (equivalente a `--allow-all`). |

Para obtener una lista completa de comandos y opciones, ejecute `copilot help`.

## Valores de disponibilidad de la herramienta

Las opciones `--available-tools` y `--excluded-tools` admiten los siguientes valores para especificar herramientas:

### Herramientas de shell

| Nombre de la herramienta | Descripción |
| --------------------------------- | -------------------------------- |
| `bash` / `powershell` | Ejecutar comandos |
| `read_bash` / `read_powershell` | Lee la salida de una sesión de shell |
| `write_bash` / `write_powershell` | Enviar entrada a una sesión de shell |
| `stop_bash` / `stop_powershell` | Finalizar una sesión de shell |
| `list_bash` / `list_powershell` | Lista las sesiones de shell activas |

### Herramientas de operación de archivos

| Nombre de la herramienta | Descripción |
| ------------- | -------------------------------------------------------------- |
| `ver` | Leer archivos o directorios |
| `crear` | Crear nuevos archivos |
| `editar` | Editar archivos mediante reemplazo de cadenas |
| `apply_patch` | Aplicar parches (utilizado por algunos modelos en lugar de `edit`/`create`) |

### Herramientas de delegación de agentes y tareas

| Nombre de la herramienta | Descripción |
| ------------- | ----------------------------- |
| `tarea` | Ejecutar subagentes |
| `read_agent` | Comprobar el estado del agente en segundo plano |
| `list_agents` | Lista de agentes disponibles |

### Otras herramientas

| Nombre de la herramienta | Descripción |
| --------------------------------- | ------------------------------------------ |
| `grep` (o `rg`) | Buscar texto en archivos |
| `glob` | Buscar archivos que coincidan con patrones |
| `web_fetch` | Obtener y analizar contenido web |
| `habilidad` | Invocar habilidades personalizadas |
| `ask_user` | Hazle una pregunta al usuario |
| `report_intent` | Informar sobre lo que el agente planea hacer |
| `show_file` | Mostrar un archivo de forma destacada |
| `fetch_copilot_cli_documentation` | Consultar la documentación de la CLI |
| `update_todo` | Actualizar la lista de tareas |
| `store_memory` | Persistir los hechos entre sesiones |
| `task_complete` | La tarea de señalización ha finalizado (solo piloto automático) |
| `exit_plan_mode` | Modo de plan de salida |
| `sql` | Consultar datos de sesión (experimental) |
| `lsp` | Refactorización del servidor de lenguaje (experimental) |

## Patrones de permisos de herramientas

Las opciones `--allow-tool` y `--deny-tool` aceptan patrones de permisos en el formato `Tipo(argumento)`. El argumento es opcional; si se omite, se aplicarán todas las herramientas de ese tipo.

| Tipo | Descripción | Ejemplos de patrones |
| ----------- | --------------------------------- | ------------------------------------------- |
| `shell` | Ejecución de comandos de shell | `shell(git push)`, `shell(git:*)`, `shell` |
| `write` | Creación o modificación de archivos | `write`, `write(src/*.ts)` |
| `read` | Lectura de archivos o directorios | `read`, `read(.env)` |
| NOMBRE DEL SERVIDOR | Invocación de la herramienta del servidor MCP | `MyMCP(create_issue)`, `MyMCP` |
| `url` | Acceso a URL mediante web-fetch o shell | `url(github.com)`, `url(https://*.api.com)` |
| `memoria` | Almacenando hechos en la memoria del agente | `memoria` |

Para las reglas de `shell`, el sufijo `:*` coincide con la raíz del comando seguida de un espacio, lo que evita coincidencias parciales. Por ejemplo, `shell(git:*)` coincide con `git push` y `git pull`, pero no con `gitea`.

Las reglas de denegación siempre tienen prioridad sobre las reglas de permiso, incluso cuando se establece `--allow-all`.

```shell
# Permitir todos los comandos de git excepto git push
copiloto --allow-tool='shell(git:*)' --deny-tool='shell(git push)'

# Permitir una herramienta de servidor MCP específica
copilot --allow-tool='MyMCP(create_issue)'

# Permitir todas las herramientas de un servidor
copiloto --permitir-herramienta='MyMCP'
```

## Variables de entorno

| Variable | Descripción |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `COPILOT_MODEL` | Configura el modelo de IA. |
| `COPILOT_ALLOW_ALL` | Establecer en `true` para permitir todos los permisos automáticamente (equivalente a `--allow-all`). |
| `COPILOT_AUTO_UPDATE` | Establezca en `false` para deshabilitar las actualizaciones automáticas. |
| `COPILOT_CUSTOM_INSTRUCTIONS_DIRS` | Lista separada por comas de directorios adicionales para instrucciones personalizadas. |
| `COPILOT_SKILLS_DIRS` | Lista separada por comas de directorios adicionales para habilidades. |
| `COPILOT_EDITOR` | Comando del editor para edición interactiva (se comprueba después de `$VISUAL` y `$EDITOR`). Por defecto, se utiliza `vi` si no se especifica ninguno. |
| `COPILOT_GITHUB_TOKEN` | Token de autenticación. Tiene prioridad sobre `GH_TOKEN` y `GITHUB_TOKEN`. |
| `COPILOT_HOME` | Sobrescribe el directorio de configuración y estado. Predeterminado: `$HOME/.copilot`. |
| `GH_TOKEN` | Token de autenticación. Tiene prioridad sobre `GITHUB_TOKEN`. |
| `GITHUB_TOKEN` | Token de autenticación. |
| `USE_BUILTIN_RIPGREP` | Establezca en `false` para usar el ripgrep del sistema en lugar de la versión incluida. |
| `PLAIN_DIFF` | Establezca en `true` para deshabilitar la representación de diferencias enriquecidas. |
| `COLORFGBG` | Opción alternativa para la detección de fondo oscuro/claro en la terminal. |
| `COPILOT_CLI_ENABLED_FEATURE_FLAGS` | Lista separada por comas de indicadores de características para habilitar (por ejemplo, `"ALGUNA_CARACTERÍSTICA,ALGUNA_OTRA_CARACTERÍSTICA"`). |

## Configuración del archivo de configuración

La configuración se propaga desde el usuario al repositorio y luego al entorno local, donde los ámbitos más específicos prevalecen sobre los más generales. Los parámetros de la línea de comandos y las variables de entorno siempre tienen la máxima prioridad.

| Alcance | Ubicación | Propósito |
| ---------- | ------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Usuario | `~/.copilot/config.json` | Valores predeterminados globales para todos los repositorios. Utilice la variable de entorno `COPILOT_HOME` para especificar una ruta alternativa. |
| Repositorio | `.github/copilot/settings.json` | Configuración compartida del repositorio (confirmada en el repositorio). |
| Local | `.github/copilot/settings.local.json` | Anulaciones personales (añadir esto a `.gitignore`). |

### Configuración de usuario (`~/.copilot/config.json`)

| Clave | Tipo | Predeterminado | Descripción |
| ---------------------------------- | --------------------------------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------- |
| `allowed_urls` | `string[]` | `[]` | URLs o dominios permitidos sin solicitud de confirmación. |
| `alt_screen` | `boolean` | `false` | Usar el búfer de pantalla alternativa del terminal. |
| `auto_update` | `boolean` | `true` | Descarga automáticamente las actualizaciones de la CLI. |
| `banner` | `"siempre"` \| `"una vez"` \| `"nunca"` | `"una vez"` | Frecuencia de visualización del banner animado. |
| `bash_env` | `boolean` | `false` | Habilita la compatibilidad con `BASH_ENV` para shells bash. |
| `bip` | `booleano` | `verdadero` | Reproduce un pitido audible cuando se requiere atención. |
| `compact_paste` | `boolean` | `true` | Contrae grandes fragmentos pegados en tokens compactos. |
| `custom_agents.default_local_only` | `booleano` | `falso` | Usar solo agentes personalizados locales. |
| `denied_urls` | `string[]` | `[]` | URLs o dominios bloqueados (tiene prioridad sobre `allowed_urls`). |
| `experimental` | `booleano` | `falso` | Habilitar funciones experimentales. |
| `include_coauthor` | `boolean` | `true` | Agrega un pie de página `Co-authored-by` a las confirmaciones de Git realizadas por el agente. |
| `companyAnnouncements` | `string[]` | `[]` | Mensajes personalizados que se muestran aleatoriamente al iniciar. |
| `log_level` | `"none"` \| `"error"` \| `"warning"` \| `"info"` \| `"debug"` \| `"all"` \| `"default"` | `"default"` | Nivel de detalle del registro. |
| `modelo` | `cadena` | varía | Modelo de IA a utilizar (ver el comando `/modelo`). |
| `powershell_flags` | `string[]` | `["-NoProfile", "-NoLogo"]` | Indicadores que se pasan a PowerShell (`pwsh`) al iniciar. Solo para Windows. |
| `reasoning_effort` | `"low"` \| `"medium"` \| `"high"` \| `"xhigh"` | `"medium"` | Nivel de esfuerzo de razonamiento para el pensamiento extendido. Los niveles más altos utilizan más capacidad de procesamiento. |
| `render_markdown` | `boolean` | `true` | Renderizar Markdown en la salida de la terminal. |
| `screen_reader` | `boolean` | `false` | Habilitar optimizaciones para lectores de pantalla. |
| `stream` | `boolean` | `true` | Habilitar respuestas en streaming. |
| `store_token_plaintext` | `boolean` | `false` | Almacena los tokens de autenticación en texto plano en el archivo de configuración cuando no hay un llavero del sistema disponible. |
| `streamer_mode` | `boolean` | `false` | Ocultar los nombres de los modelos de vista previa y los detalles de la cuota (útil al grabar). |
| `tema` | `automático` | `oscuro` | `claro` | `automático` | Tema de color de la terminal. |
| `trusted_folders` | `string[]` | `[]` | Carpetas con acceso a archivos previamente concedido. |
| `update_terminal_title` | `boolean` | `true` | Muestra la intención actual en el título de la terminal. |

### Configuración del repositorio (`.github/copilot/settings.json`)

La configuración del repositorio se aplica a todos los usuarios que trabajan en él. Solo se admite un subconjunto de la configuración a nivel de repositorio. Las claves no compatibles se ignoran.

| Clave | Tipo | Comportamiento de fusión | Descripción | |
| ------------------------ | ------------------------- | --------------------------------------------- | -------------------------------------------------------------- | ----------------------------------------- |
| `companyAnnouncements` | `string[]` | Reemplazado: el repositorio tiene prioridad | Mensajes mostrados aleatoriamente al iniciar. | |
| `enabledPlugins` | `Record<string, boolean>` | Fusionado: el repositorio anula al usuario para la misma clave | Instalación automática declarativa de complementos. | |
| `extraKnownMarketplaces` | `Record<string, {...}>` | Fusionado: el repositorio anula al usuario para la misma clave | Mercados de complementos disponibles en este repositorio. | |
| `mercados` | `Registro<cadena, {...}>` | Fusionado: el repositorio anula al usuario para la misma clave | Mercados de complementos (obsoleto: use `extraKnownMarketplaces`). | <!-- markdownlint-disable-line GHD046 --> |

### Configuración local (`.github/copilot/settings.local.json`)

Crea el archivo `.github/copilot/settings.local.json` en el repositorio para las configuraciones personales que no deben confirmarse. Agrega este archivo a `.gitignore`.

El archivo de configuración local utiliza el mismo esquema que el archivo de configuración del repositorio (`.github/copilot/settings.json`) y tiene prioridad sobre él.

## Referencia de ganchos

Los hooks son comandos externos que se ejecutan en puntos específicos del ciclo de vida durante una sesión, lo que permite la automatización personalizada, los controles de seguridad y las integraciones. Los archivos de configuración de hooks se cargan automáticamente desde `.github/hooks/*.json` en tu repositorio.

### Formato de configuración del gancho

Los archivos de configuración de hooks utilizan el formato JSON con la versión `1`.

#### Ganchos de comando

Los hooks de comando ejecutan scripts de shell y son compatibles con todos los tipos de hooks.

```json
{
  "versión": 1,
  "ganchos": {
    "preToolUse": [
      {
        "tipo": "comando",
        "bash": "tu-comando-bash",
        "powershell": "tu-comando-de-powershell",
        "cwd": "directorio/de/trabajo/opcional",
        "env": { "VAR": "valor" },
        "timeoutSec": 30
      }
    ]
  }
}
```

| Campo | Tipo | Obligatorio | Descripción |
| ------------ | ----------- | -------------------------- | ---------------------------------------------------------------------------- |
| `tipo` | `"comando"` | Sí | Debe ser `"comando"`. |
| `bash` | cadena | Uno de `bash`/`powershell` | Comando de shell para Unix. |
| `powershell` | cadena | Uno de `bash`/`powershell` | Comando de shell para Windows. |
| `cwd` | cadena | No | Directorio de trabajo para el comando (relativo a la raíz del repositorio o absoluto). |
| `env` | objeto | No | Variables de entorno a configurar (admite expansión de variables). |
| `timeoutSec` | número | No | Tiempo de espera en segundos. Predeterminado: `30`. |

#### Ganchos de solicitud

Los ganchos de solicitud envían automáticamente el texto como si el usuario lo hubiera escrito. Solo son compatibles con `sessionStart` y se ejecutan antes de cualquier solicitud inicial pasada mediante `--prompt`. El texto puede ser una solicitud en lenguaje natural o un comando de barra diagonal.

```json
{
  "versión": 1,
  "ganchos": {
    "sessionStart": [
      {
        "tipo": "propuesta",
        "prompt": "Tu texto de solicitud o comando /barra"
      }
    ]
  }
}
```

| Campo | Tipo | Obligatorio | Descripción |
| -------- | ---------- | -------- | -------------------------------------------------------------------- |
| `type` | `"prompt"` | Sí | Debe ser `"prompt"`. |
| `prompt` | cadena | Sí | Texto a enviar: puede ser un mensaje en lenguaje natural o un comando de barra. |

### Eventos de gancho

| Evento | Se activa cuando | Salida procesada |
| --------------------- | --------------------------------- | --------------------------------------- |
| `sessionStart` | Se inicia una sesión nueva o reanudada. | No |
| `sessionEnd` | La sesión finaliza. | No |
| `userPromptSubmitted` | El usuario envía una solicitud. | No |
| `preToolUse` | Antes de que se ejecute cada herramienta. | Sí: puede permitir, denegar o modificar. |
| `postToolUse` | Después de que cada herramienta finalice. | No |
| `agentStop` | El agente principal finaliza su turno. | Sí, puede bloquear y forzar la continuación. |
| `subagentStop` | Un subagente finaliza. | Sí, puede bloquear y forzar la continuación. |
| `errorOccurred` | Se produjo un error durante la ejecución. | No |

### control de decisiones `preToolUse`

El gancho `preToolUse` puede controlar la ejecución de la herramienta escribiendo un objeto JSON en la salida estándar.

| Campo | Valores | Descripción |
| -------------------------- | ---------------------------- | -------------------------------------------------------------- |
| `permissionDecision` | `"allow"`, `"deny"`, `"ask"` | Indica si la herramienta se ejecuta. La salida vacía utiliza el comportamiento predeterminado. |
| `permissionDecisionReason` | cadena | Motivo que se muestra al agente. Obligatorio cuando la decisión es "denegar". |
| `modifiedArgs` | objeto | Sustituye los argumentos de la herramienta por otros que se usarán en lugar de los originales. |

### Control de decisiones `agentStop` / `subagentStop`

| Campo | Valores | Descripción |
| ---------- | -------------------- | ----------------------------------------------------------------- |
| `decisión` | `"bloquear"`, `"permitir"` | `"bloquear"` fuerza a otro agente a girar usando `razón` como indicación. |
| `razón` | cadena | Indica el siguiente turno cuando `decisión` sea `"bloquear"`. |

### Nombres de herramientas para la coincidencia de ganchos

| Nombre de la herramienta | Descripción |
| ------------ | --------------------------------- |
| `bash` | Ejecuta comandos de shell (Unix). |
| `powershell` | Ejecuta comandos de shell (Windows). |
| `view` | Leer el contenido del archivo. |
| `editar` | Modificar el contenido del archivo. |
| `crear` | Crear nuevos archivos. |
| `glob` | Buscar archivos por patrón. |
| `grep` | Buscar en el contenido del archivo. |
| `web_fetch` | Obtener páginas web. |
| `tarea` | Ejecutar tareas de subagente. |

Si se configuran varios ganchos del mismo tipo, se ejecutan en orden. Para `preToolUse`, si algún gancho devuelve `"deny"`, la herramienta se bloquea. Los fallos de los ganchos (códigos de salida distintos de cero o tiempos de espera agotados) se registran y se omiten; nunca bloquean la ejecución del agente.

## Configuración del servidor MCP

Los servidores MCP proporcionan herramientas adicionales al agente CLI. Configure los servidores persistentes en `~/.copilot/mcp-config.json`. Use `--additional-mcp-config` para agregar servidores para una sola sesión.

### Tipos de transporte

| Tipo | Descripción | Campos obligatorios |
| ----------------- | ------------------------------------------------- | ----------------- |
| `local` / `stdio` | Proceso local que se comunica a través de stdin/stdout. | `comando`, `argumentos` |
| `http` | Servidor remoto que utiliza transporte HTTP en flujo continuo. | `url` |
| `sse` | Servidor remoto que utiliza el transporte Server-Sent Events. | `url` |

### Campos de configuración del servidor local

| Campo | Obligatorio | Descripción |
| --------- | -------- | ---------------------------------------------------------------------------------- |
| `comando` | Sí | Comando para iniciar el servidor. |
| `args` | Sí | Argumentos del comando (matriz). |
| `tools` | Sí | Herramientas a habilitar: `["*"]` para todas, o una lista de nombres de herramientas específicas. |
| `env` | No | Variables de entorno. Admite la expansión `$VAR`, `${VAR}` y `${VAR:-default}`. |
| `cwd` | No | Directorio de trabajo del servidor. |
| `timeout` | No | Tiempo de espera de la llamada a la herramienta en milisegundos. |
| `type` | No | `"local"` o `"stdio"`. Predeterminado: `"local"`. |

### Campos de configuración del servidor remoto

| Campo | Obligatorio | Descripción |
| ------------------- | -------- | ---------------------------------------------------- |
| `tipo` | Sí | `"http"` o `"sse"`. |
| `url` | Sí | URL del servidor. |
| `herramientas` | Sí | Herramientas para habilitar. |
| `headers` | No | Encabezados HTTP. Admite expansión de variables. |
| `oauthClientId` | No | ID de cliente OAuth estático (omite el registro dinámico). |
| `oauthPublicClient` | No | Indica si el cliente OAuth es público. Valor predeterminado: `true`. |
| `timeout` | No | Tiempo de espera de la llamada a la herramienta en milisegundos. |

### Mapeo de filtros

Controla cómo se procesa la salida de la herramienta MCP mediante el campo `filterMapping` en la configuración del servidor.

| Modo | Descripción |
| ------------------- | --------------------------------------------- |
| `ninguno` | Sin filtrado. |
| `markdown` | Formatear la salida como Markdown. |
| `hidden_characters` | Elimina los caracteres ocultos o de control. Predeterminado. |

### Servidores MCP integrados

La interfaz de línea de comandos (CLI) incluye servidores MCP integrados que están disponibles sin necesidad de configuración adicional.

| Servidor | Descripción |
| ------------------- | ---------------------------------------------------------------------------------------- |
| `github-mcp-server` | Integración con la API de GitHub: incidencias, solicitudes de extracción, confirmaciones, búsqueda de código y GitHub Actions. |
| `dramaturgo` | Automatización del navegador: navegación, clic, escritura, captura de pantalla y manejo de formularios. |
| `fetch` | Solicitudes HTTP a través de la herramienta `fetch`. |
| `tiempo` | Utilidades de tiempo: `get_current_time` y `convert_time`. |

Utilice `--disable-builtin-mcps` para deshabilitar todos los servidores integrados, o `--disable-mcp-server SERVER-NAME` para deshabilitar uno específico.

### Niveles de confianza del servidor MCP

Los servidores MCP se cargan desde múltiples fuentes, cada una con un nivel de confianza diferente.

| Fuente | Nivel de confianza | Se requiere revisión |
| ------------------------------------------------- | ------------ | ------------------- |
| Integrado | Alto | No |
| Repositorio (`.github/mcp.json`) | Medio | Recomendado |
| Espacio de trabajo (`.mcp.json`, `.vscode/mcp.json`) | Medio | Recomendado |
| Contenedor de desarrollo (`.devcontainer/devcontainer.json`) | Medio | Recomendado |
| Configuración del usuario (`~/.copilot/mcp-config.json`) | Definido por el usuario | Responsabilidad del usuario |
| Servidores remotos | Bajo | Siempre |

Todas las invocaciones de herramientas MCP requieren permiso explícito. Esto se aplica incluso a las operaciones de solo lectura en servicios externos.

## Referencia de habilidades

Las habilidades son archivos Markdown que amplían las funcionalidades de la interfaz de línea de comandos (CLI). Cada habilidad reside en su propio directorio, que contiene un archivo `SKILL.md`. Al invocarse (mediante `/SKILL-NAME` o automáticamente por el agente), el contenido de la habilidad se inserta en la conversación.

### Campos de información preliminar de habilidades

| Campo | Tipo | Obligatorio | Descripción |
| -------------------------- | ------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `nombre` | cadena | Sí | Identificador único para la habilidad. Solo letras, números y guiones. Máximo 64 caracteres. |
| `descripción` | cadena | Sí | Qué hace la habilidad y cuándo usarla. Máximo 1024 caracteres. |
| `allowed-tools` | cadena o cadena\[] | No | Lista separada por comas o matriz YAML de herramientas que se permiten automáticamente cuando la habilidad está activa. Use `"*"` para todas las herramientas. |
| `user-invocable` | booleano | No | Indica si los usuarios pueden invocar la habilidad con `/SKILL-NAME`. Valor predeterminado: `true`. |
| `disable-model-invocation` | booleano | No | Impide que el agente invoque automáticamente esta habilidad. Valor predeterminado: `false`. |

### Ubicaciones de habilidades

Las habilidades se cargan desde estas ubicaciones en orden de prioridad (el primero que se encuentre ganará en caso de nombres duplicados).

| Ubicación | Alcance | Descripción |
| ------------------------ | --------- | ----------------------------------------- |
| `.github/skills/` | Proyecto | Habilidades específicas del proyecto. |
| `.agents/skills/` | Proyecto | Ubicación alternativa del proyecto. |
| `.claude/skills/` | Proyecto | Ubicación compatible con Claude. |
| Directorio padre `.github/skills/` | Heredado | Soporte para directorio padre de monorepo. |
| `~/.copilot/skills/` | Personal | Habilidades personales para todos los proyectos. |
| `~/.claude/skills/` | Personal | Ubicación personal compatible con Claude. |
Directorios de plugins | Plugin | Habilidades de los plugins instalados.
| `COPILOT_SKILLS_DIRS` | Personalizado | Directorios adicionales (separados por comas). |

### Comandos (formato de habilidad alternativo)

Los comandos son una alternativa a las habilidades almacenadas como archivos `.md` individuales en `.claude/commands/`. El nombre del comando se deriva del nombre del archivo. Los archivos de comandos utilizan un formato simplificado (no se requiere el campo `name`) y admiten `description`, `allowed-tools` y `disable-model-invocation`. Los comandos tienen menor prioridad que las habilidades con el mismo nombre.

## Referencia de agentes personalizados

Los agentes personalizados son agentes de IA especializados definidos en archivos Markdown. El nombre del archivo (sin la extensión) se convierte en el ID del agente. Utilice `.agent.md` o `.md` como extensión de archivo.

### Agentes integrados

| Agente | Modelo predeterminado | Descripción |
| ----------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `code-review` | claude-sonnet-4.5 | Revisión de código con alta relación señal/ruido. Analiza las diferencias en busca de errores, problemas de seguridad y errores lógicos. |
| `explore` | claude-haiku-4.5 | Exploración rápida del código fuente. Busca archivos, lee el código y responde preguntas. Devuelve respuestas concisas de menos de 300 palabras. Se puede ejecutar en paralelo de forma segura. |
| `general-purpose` | claude-sonnet-4.5 | Agente con plena capacidad para tareas complejas de varios pasos. Se ejecuta en una ventana de contexto separada. |
| `investigación` | claude-sonnet-4.6 | Agente de investigación profunda. Genera un informe basado en la información de tu código fuente, en repositorios relevantes y en la web. |
| `tarea` | claude-haiku-4.5 | Ejecución de comandos (pruebas, compilaciones, análisis estáticos). Devuelve un breve resumen si tiene éxito, la salida completa si falla. |

### Campos de metadatos del agente personalizado

| Campo | Tipo | Obligatorio | Descripción |
| ------------- | --------- | -------- | ----------------------------------------------------------------------------- |
| `descripción` | cadena | Sí | Descripción que se muestra en la lista de agentes y en la herramienta `t ask`. |
| `inferir` | booleano | No | Permite la delegación automática por parte del agente principal. Valor predeterminado: `verdadero`. |
| `mcp-servers` | objeto | No | Servidores MCP a los que conectarse. Utiliza el mismo esquema que `~/.copilot/mcp-config.json`. |
| `modelo` | cadena | No | Modelo de IA para este agente. Cuando no se establece, hereda el modelo del agente externo. |
| `nombre` | cadena | No | Nombre para mostrar. Por defecto, se utiliza el nombre del archivo. |
| `tools` | string\[] | No | Herramientas disponibles para el agente. Predeterminado: `["*"]` (todas las herramientas). |

### Ubicaciones de agentes personalizados

| Alcance | Ubicación |
| ------- | ------------------------------------------- |
| Proyecto | `.github/agents/` o `.claude/agents/` |
| Usuario | `~/.copilot/agents/` o `~/.claude/agents/` |
| Complemento | `<plugin>/agentes/` |

Los agentes a nivel de proyecto tienen prioridad sobre los agentes a nivel de usuario. Los agentes de complemento tienen la prioridad más baja.

## Respuestas de aprobación de permisos

Cuando la interfaz de línea de comandos (CLI) solicite permiso para ejecutar una operación, puede responder con las siguientes claves.

| Clave | Efecto |
| --- | ------------------------------------------------------- |
| `y` | Permitir esta solicitud específica una sola vez. |
| `n` | Deniega esta solicitud específica una sola vez. |
| `!` | Permitir todas las solicitudes similares durante el resto de la sesión. |
| `#` | Denegar todas las solicitudes similares durante el resto de la sesión. |
| `?` | Mostrar información detallada sobre la solicitud. |

Las aprobaciones de sesión se restablecen al ejecutar `/clear` o al iniciar una nueva sesión.

| Bandera | Nivel | Descripción |
| ------------------- | -------------- | ------------------------------------------ |
| `MODO_AUTOPILOTE` | `experimental` | Modo de funcionamiento autónomo. |
| `AGENTES_EN_SEGUNDO_PARTIDO` | `personal` | Ejecutar agentes en segundo plano. |
| `QUEUED_COMMANDS` | `staff` | Poner en cola los comandos mientras el agente está en ejecución. |
| `LSP_TOOLS` | `on` | Herramientas del protocolo del servidor de lenguaje. |
| `PLAN_COMMAND` | `on` | Modo de planificación interactiva. |
| `AGENTIC_MEMORY` | `on` | Memoria persistente entre sesiones. |
| `AGENTES_PERSONALIZADOS` | `activado` | Definiciones de agentes personalizados. |

## Monitoreo de OpenTelemetry

La CLI de Copilot puede exportar trazas y métricas a través de [OpenTelemetry](https://opentelemetry.io/) (OTel), lo que le brinda visibilidad de las interacciones del agente, las llamadas LLM, las ejecuciones de herramientas y el uso de tokens. Todos los nombres y atributos de las señales siguen las [Convenciones semánticas de GenAI de OTel](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/gen-ai/).

OTel está desactivado por defecto y no consume recursos. Se activa cuando se cumple alguna de las siguientes condiciones:

* `COPILOT_OTEL_ENABLED=true`
* `OTEL_EXPORTER_OTLP_ENDPOINT` está configurado
* Se ha establecido `COPILOT_OTEL_FILE_EXPORTER_PATH`.

### Variables de entorno de OTel

| Variable | Predeterminado | Descripción |
| ---------------------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------ |
| `COPILOT_OTEL_ENABLED` | `false` | Habilita explícitamente OTel. No es necesario si `OTEL_EXPORTER_OTLP_ENDPOINT` está configurado. |
| `OTEL_EXPORTER_OTLP_ENDPOINT` | — | URL del punto final OTLP. Al configurar esto, habilita OTel automáticamente. |
| `COPILOT_OTEL_EXPORTER_TYPE` | `otlp-http` | Tipo de exportador: `otlp-http` o `file`. Selecciona automáticamente `file` cuando se establece `COPILOT_OTEL_FILE_EXPORTER_PATH`. |
| `OTEL_SERVICE_NAME` | `github-copilot` | Nombre del servicio en los atributos del recurso. |
| `OTEL_RESOURCE_ATTRIBUTES` | — | Atributos de recursos adicionales como pares `clave=valor` separados por comas. Utilice la codificación porcentual para caracteres especiales. |
| `OTEL_INSTRUMENTATION_GENAI_CAPTURE_MESSAGE_CONTENT` | `false` | Capturar el contenido completo de la solicitud y la respuesta. Consulte [Captura de contenido](#content-capture). |
| `OTEL_LOG_LEVEL` | — | Nivel de registro de diagnóstico de OTel: `NINGUNO`, `ERROR`, `ADVERTENCIA`, `INFORMACIÓN`, `DEPURACIÓN`, `VERBOSE`, `TODOS`. |
| `COPILOT_OTEL_FILE_EXPORTER_PATH` | — | Escribe todas las señales en este archivo como líneas JSON. Al configurar esto, habilita OTel automáticamente. |
| `COPILOT_OTEL_SOURCE_NAME` | `github.copilot` | Nombre del ámbito de instrumentación para el rastreador y el medidor. |
| `OTEL_EXPORTER_OTLP_HEADERS` | — | Encabezados de autenticación para el exportador OTLP (por ejemplo, `Authorization=Bearer token`). |

### Rastros

El entorno de ejecución genera un árbol de conexiones jerárquico para cada interacción del agente. Cada árbol contiene una conexión raíz `invoke_agent`, con conexiones hijas `chat` y `execute_tool`.

#### Atributos span de `invoke_agent`

Envuelve toda la invocación del agente: todas las llamadas LLM y ejecuciones de herramientas para un mensaje de usuario. Tipo de span: `CLIENTE`.

| Atributo | Descripción |
| ------------------------------------------ | ---------------------------------------------------- |
| `gen_ai.operation.name` | `invoke_agent` |
| `gen_ai.provider.name` | Proveedor (por ejemplo, `github`, `anthropic`) |
| `gen_ai.agent.id` | Identificador de sesión |
| `gen_ai.agent.name` | Nombre del agente (solo subagentes) |
| `gen_ai.agent.description` | Descripción del agente (solo subagentes) |
| `gen_ai.agent.version` | Versión de tiempo de ejecución |
| `gen_ai.conversation.id` | Identificador de sesión |
| `gen_ai.request.model` | Modelo solicitado |
| `gen_ai.response.model` | Modelo resuelto |
| `gen_ai.response.id` | ID de la última respuesta |
| `gen_ai.response.finish_reasons` | `["stop"]` o `["error"]` |
| `gen_ai.usage.input_tokens` | Total de tokens de entrada (todos los turnos) |
| `gen_ai.usage.output_tokens` | Total de tokens de salida (todos los turnos) |
| `gen_ai.usage.cache_read.input_tokens` | Tokens de entrada almacenados en caché leídos |
| `gen_ai.usage.cache_creation.input_tokens` | Tokens de entrada en caché creados |
| `github.copilot.turn_count` | Número de viajes de ida y vuelta del LLM |
| `github.copilot.cost` | Costo monetario |
| `github.copilot.aiu` | Unidades de IA consumidas |
| `servidor.dirección` | Nombre de host del servidor |
| `servidor.puerto` | Puerto del servidor |
| `error.type` | Nombre de la clase de error (en caso de error) |
| `gen_ai.input.messages` | Mensajes de entrada completos en formato JSON (solo captura de contenido) |
| `gen_ai.output.messages` | Mensajes de salida completos en formato JSON (solo captura de contenido) |
| `gen_ai.system_instructions` | Contenido del mensaje del sistema como JSON (solo captura de contenido) |
| `gen_ai.tool.definitions` | Esquemas de herramientas como JSON (solo captura de contenido) |

#### Atributos span de `chat`

Un segmento por solicitud LLM. Tipo de segmento: `CLIENTE`.

| Atributo | Descripción |
| ------------------------------------------ | ----------------------------------------------------- |
| `gen_ai.operation.name` | `chat` |
| `gen_ai.provider.name` | Nombre del proveedor |
| `gen_ai.request.model` | Modelo solicitado |
| `gen_ai.conversation.id` | Identificador de sesión |
| `gen_ai.response.id` | ID de respuesta |
| `gen_ai.response.model` | Modelo resuelto |
| `gen_ai.response.finish_reasons` | Razones para detener la respuesta |
| `gen_ai.usage.input_tokens` | Tokens de entrada en este turno |
| `gen_ai.usage.output_tokens` | Tokens de salida en este turno |
| `gen_ai.usage.cache_read.input_tokens` | Tokens almacenados en caché leídos |
| `gen_ai.usage.cache_creation.input_tokens` | Tokens en caché creados |
| `github.copilot.cost` | Coste del turno |
| `github.copilot.aiu` | Unidades de IA consumidas en este turno |
| `github.copilot.server_duration` | Duración del lado del servidor |
| `github.copilot.initiator` | Iniciador de la solicitud |
| `github.copilot.turn_id` | Identificador de giro |
| `github.copilot.interaction_id` | Identificador de interacción |
| `servidor.dirección` | Nombre de host del servidor |
| `servidor.puerto` | Puerto del servidor |
| `error.type` | Nombre de la clase de error (en caso de error) |
| `gen_ai.input.messages` | Mensajes de solicitud completos en formato JSON (solo captura de contenido) |
| `gen_ai.output.messages` | Mensajes de respuesta completos en formato JSON (solo captura de contenido) |
| `gen_ai.system_instructions` | Contenido del mensaje del sistema como JSON (solo captura de contenido) |

#### Atributos span de `execute_tool`

Un segmento por llamada a la herramienta. Tipo de segmento: `INTERNAL`.

| Atributo | Descripción |
| ---------------------------- | --------------------------------------------------- |
| `gen_ai.operation.name` | `execute_tool` |
| `gen_ai.provider.name` | Nombre del proveedor (cuando esté disponible) |
| `gen_ai.tool.name` | Nombre de la herramienta (por ejemplo, `readFile`) |
| `gen_ai.tool.type` | `función` |
| `gen_ai.tool.call.id` | Identificador de llamada a la herramienta |
| `gen_ai.tool.description` | Descripción de la herramienta |
| `error.type` | Nombre de la clase de error (en caso de error) |
| `gen_ai.tool.call.arguments` | Argumentos de entrada de la herramienta como JSON (solo captura de contenido) |
| `gen_ai.tool.call.result` | Salida de la herramienta en formato JSON (solo captura de contenido) |

### Métricas

#### Métricas de convención de GenAI

| Métrico | Tipo | Unidad | Descripción |
| ----------------------------------------------- | --------- | ------ | ------------------------------------------ |
| `gen_ai.client.operation.duration` | Histograma | s | Duración de la llamada a la API de LLM y la invocación del agente |
| `gen_ai.client.token.usage` | Histograma | tokens | Recuento de tokens por tipo (`entrada`/`salida`) |
| `gen_ai.client.operation.time_to_first_chunk` | Histograma | s | Tiempo para recibir el primer fragmento de transmisión |
| `gen_ai.client.operation.time_per_output_chunk` | Histograma | s | Latencia entre fragmentos después del primer fragmento |

#### Métricas específicas del proveedor

| Métrico | Tipo | Unidad | Descripción |
| ----------------------------------- | --------- | ----- | ---------------------------------------------------- |
| `github.copilot.tool.call.count` | Contador | llamadas | Invocaciones de herramientas por `gen_ai.tool.name` y `success` |
| `github.copilot.tool.call.duration` | Histograma | s | Latencia de ejecución de la herramienta por `gen_ai.tool.name` |
| `github.copilot.agent.turn.count` | Histograma | giros | Viajes de ida y vuelta LLM por invocación del agente |

### Eventos de expansión

Eventos del ciclo de vida registrados en el segmento `chat` o `invoke_agent` activo.

| Evento | Descripción | Atributos clave |
| -------------------------------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `github.copilot.session.truncation` | El historial de la conversación se truncó | `github.copilot.token_limit`, `github.copilot.pre_tokens`, `github.copilot.post_tokens`, `github.copilot.tokens_removed`, `github.copilot.messages_removed` |
| `github.copilot.session.compaction_start` | Se inició la compactación del historial | Ninguno |
| `github.copilot.session.compaction_complete` | Compactación del historial completada | `github.copilot.success`, `github.copilot.pre_tokens`, `github.copilot.post_tokens`, `github.copilot.tokens_removed`, `github.copilot.messages_removed` |
| `github.copilot.skill.invoked` | Se invocó una habilidad | `github.copilot.skill.name`, `github.copilot.skill.path`, `github.copilot.skill.plugin_name`, `github.copilot.skill.plugin_version` |
| `github.copilot.session.shutdown` | La sesión se está cerrando | `github.copilot.shutdown_type`, `github.copilot.total_premium_requests`, `github.copilot.lines_added`, `github.copilot.lines_removed`, `github.copilot.files_modified_count` |
| `github.copilot.session.abort` | El usuario canceló la operación actual | `github.copilot.abort_reason` |
| `excepción` | Error de sesión | `github.copilot.error_type`, `github.copilot.error_status_code`, `github.copilot.error_provider_call_id` |

### Atributos del recurso

Todas las señales portan estos atributos de recurso.

| Atributo | Valor |
| ----------------- | ------------------------------------------------------- |
| `service.name` | `github-copilot` (configurable mediante `OTEL_SERVICE_NAME`) |
| `service.version` | Versión en tiempo de ejecución |

### Captura de contenido

Por defecto, no se captura el contenido de las solicitudes, las respuestas ni los argumentos de las herramientas; solo se capturan los metadatos, como los nombres de los modelos, el número de tokens y la duración. Para capturar el contenido completo, configure `OTEL_INSTRUMENTATION_GENAI_CAPTURE_MESSAGE_CONTENT=true`.

> \[!ADVERTENCIA]
La captura de contenido puede incluir información confidencial como código, contenido de archivos y mensajes al usuario. Habilite esta función únicamente en entornos de confianza.

Cuando se habilita la captura de contenido, se completan los siguientes atributos.

| Atributo | Contenido |
| ---------------------------- | ----------------------------- |
| `gen_ai.input.messages` | Mensajes de solicitud completos (JSON) |
| `gen_ai.output.messages` | Mensajes de respuesta completos (JSON) |
| `gen_ai.system_instructions` | Contenido del mensaje del sistema (JSON) |
| `gen_ai.tool.definitions` | Esquemas de herramientas (JSON) |
| `gen_ai.tool.call.arguments` | Argumentos de entrada de la herramienta |
| `gen_ai.tool.call.result` | Salida de la herramienta |

## Lecturas adicionales

* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)
* [Referencia del complemento CLI de GitHub Copilot](/en/copilot/reference/copilot-cli-reference/cli-plugin-reference)
* [Referencia programática de la CLI de GitHub Copilot](/en/copilot/reference/copilot-cli-reference/cli-programmatic-reference)# About versions of GitHub Docs

You can read documentation that reflects the GitHub product you're currently using.

## About versions of GitHub Docs

GitHub offers different plans for storing and collaborating on code. The plan you use determines which features are available to you. For more information, see [GitHub's plans](/en/get-started/learning-about-github/githubs-plans).

This website, GitHub Docs, provides documentation for all of GitHub's plans. If the content you're reading applies to more than one plan, you can choose the version of the documentation that's relevant to you by selecting the plan you're currently using.

At the top of a page on GitHub Docs, select the dropdown menu and click a plan. If your browser window is not wide enough to display the full navigation bar, you may need to click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Open Menu Bar" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> first.

![Screenshot of the header of GitHub Docs. The "Version" dropdown menu is expanded and highlighted with an orange outline.](/assets/images/help/docs/version-picker.png)

> \[!NOTE]
> You can try changing the version now. You're viewing the **Free, Pro, & Team** version of this article.

## Determining which GitHub product you use

You can determine which GitHub plan you're currently using by reviewing the URL in the address bar of your browser and the heading for the GitHub website you're on.

You may use more than one GitHub plan. For example, you might contribute to open source on GitHub.com and collaborate on code on your employer's GitHub Enterprise Server instance. You may need to view different versions of the same article at different times, depending on the problem you're currently trying to solve.

### GitHub.com plans or GitHub Enterprise Cloud

If you access GitHub at <https://github.com>, you're either using the features of a Free, Pro, or Team plan, or you're using GitHub Enterprise Cloud.

On GitHub.com, each account has its own plan. Each personal account has an associated plan that provides access to certain features, and each organization has a different associated plan. If your personal account is a member of an organization on GitHub, you may have access to different features when you use resources owned by that organization than when you use resources owned by your personal account. For more information, see [Types of GitHub accounts](/en/get-started/learning-about-github/types-of-github-accounts).

If you don't know whether an organization uses GitHub Enterprise Cloud, ask an organization owner. For more information, see [Viewing people's roles in an organization](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/viewing-peoples-roles-in-an-organization).

### GHE.com

If you access GitHub at a subdomain of GHE.com, such as `octocorp.ghe.com`, you're part of an enterprise that uses GitHub Enterprise Cloud with data residency. You should use the "GitHub Enterprise Cloud" version of GitHub Docs.

Because you're using a managed user account, certain parts of the documentation may not apply to you. See [Abilities and restrictions of managed user accounts](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/abilities-and-restrictions-of-managed-user-accounts).

If you see references to "github.com" in the documentation, you may need to substitute these references for your enterprise's subdomain on GHE.com. For example, you will make API calls to `https://api.SUBDOMAIN.ghe.com`, rather than `https://api.github.com`.

### GitHub Enterprise Server

If you access GitHub at a URL **other than** <https://github.com>, `https://*.github.us`, or `https://*.ghe.com`, you're using GitHub Enterprise Server. For example, you may access GitHub Enterprise Server at `https://github.YOUR-COMPANY-NAME.com`. Your administrators may choose a URL that doesn't include the word "GitHub."

In a wide browser window, the word "Enterprise" immediately follows the GitHub logo on the left side of the header.

![Screenshot of the header of any page on GitHub. The GitHub logo and "Enterprise" are highlighted with an orange outline.](/assets/images/help/docs/header-ghes.png)

You can view the version of GitHub Enterprise Server that you're using in the footer of any page.

![Screenshot of the footer of GitHub Enterprise Server. "GitHub Enterprise Server 3.7.5" is highlighted with an orange outline.](/assets/images/help/docs/ghes-version-in-footer.png)---
title: '{% data variables.copilot.copilot_cli %}'
shortTitle: '{% data variables.copilot.copilot_cli_short %}'
intro: Use {% data variables.product.prodname_copilot_short %} directly from your terminal to answer questions, write and debug code, and interact with {% data variables.product.github %}.
versions:
  feature: copilot
contentType: how-tos
layout: bespoke-landing
heroImage: /assets/images/banner-images/hero-4
sidebarLink:
  text: All articles
  href: /copilot/how-tos/copilot-cli
introLinks:
  overview: /copilot/concepts/agents/copilot-cli/about-copilot-cli
  quickstart: /copilot/how-tos/copilot-cli/cli-getting-started
children:
  - /cli-getting-started
  - /cli-best-practices
  - /set-up-copilot-cli
  - /allowing-tools
  - /automate-copilot-cli
  - /customize-copilot
  - /use-copilot-cli-agents
  - /administer-copilot-cli-for-your-enterprise
  - /speeding-up-task-completion
  - /chronicle
  - /content/copilot/concepts/agents/copilot-cli/about-copilot-cli
  - /content/copilot/concepts/agents/copilot-cli/comparing-cli-features
  - /content/copilot/concepts/agents/about-agent-skills
  - /content/copilot/concepts/agents/copilot-cli/about-cli-plugins
  - /content/copilot/concepts/agents/copilot-cli/autopilot
  - /content/copilot/concepts/agents/copilot-cli/fleet
  - /content/copilot/concepts/agents/copilot-cli/research
  - /content/copilot/concepts/agents/copilot-cli/chronicle
  - /set-up-copilot-cli/install-copilot-cli
  - /set-up-copilot-cli/configure-copilot-cli
  - /automate-copilot-cli/quickstart
  - /automate-copilot-cli/automate-with-actions
  - /automate-copilot-cli/run-cli-programmatically
  - /customize-copilot/add-custom-instructions
  - /customize-copilot/create-custom-agents-for-cli
  - /customize-copilot/create-skills
  - /customize-copilot/plugins-creating
  - /customize-copilot/plugins-finding-installing
  - /customize-copilot/plugins-marketplace
  - /customize-copilot/overview
  - /customize-copilot/use-hooks
  - /content/copilot/reference/copilot-cli-reference/cli-command-reference
  - /content/copilot/reference/copilot-cli-reference/cli-plugin-reference
  - /content/copilot/reference/copilot-cli-reference/cli-programmatic-reference
  - /content/copilot/reference/copilot-cli-reference/acp-server
  - /content/copilot/reference/hooks-configuration
  - /content/copilot/tutorials/copilot-cli-hooks
  - /content/copilot/responsible-use/copilot-cli
carousels:
  recommended:
    - /copilot/how-tos/copilot-cli/use-copilot-cli-agents/overview
    - /copilot/how-tos/copilot-cli/cli-best-practices
    - /copilot/reference/copilot-cli-reference/cli-command-reference
includedCategories:
  - Quickstarts
  - Learn about Copilot CLI
  - Configure Copilot CLI
  - Build with Copilot CLI
  - Administer Copilot CLI
---# Contributing to Agentic Workflow Firewall

Thank you for your interest in contributing! We welcome contributions from the community and are excited to work with you.

## 🚀 Quick Start for Contributors

1. **Fork and clone the repository**
   ```bash
   git clone https://github.com/yourname/gh-aw-firewall.git
   cd awf
   ```

2. **Set up the development environment**
   ```bash
   # Install dependencies
   npm install

   # Build the project
   npm run build

3. **Submit your contribution**
   - Create a new branch for your feature or fix
   - Make your changes
   - Run tests and linter to ensure all checks pass
   - Submit a pull request

## 🛠️ Development Setup

### Prerequisites
- **Docker**: Must be running for integration tests
- **Node.js**: v20.12.0+ and npm
- **Root/Sudo Access**: Required for testing iptables functionality
- **Git**: For version control

### Build Commands
- `npm install` - Install dependencies
- `npm run build` - Build TypeScript to dist/
- `npm run dev` - Watch mode (rebuilds on changes)
- `npm test` - Run tests
- `npm test:watch` - Run tests in watch mode
- `npm run lint` - Lint TypeScript files
- `npm run clean` - Clean build artifacts

## 📝 How to Contribute

### Reporting Issues
- Use the GitHub issue tracker to report bugs
- Include detailed steps to reproduce the issue
- Include version information (`awf --version`)
- Include Docker version (`docker --version`)
- Include relevant log output (use `--log-level debug`)

### Suggesting Features
- Open an issue describing your feature request
- Explain the use case and how it would benefit users
- Include examples if applicable

### Contributing Code

#### Code Style
- Follow TypeScript best practices
- Use `npm run lint` to check code style
- Ensure all tests pass (`npm test`)
- Write tests for new functionality
- Add JSDoc comments for public APIs

#### Logging
When adding log output, always use the logger from `src/logger.ts`:

```typescript
import { logger } from './logger';

// Use appropriate log levels
logger.info('Starting operation...');
logger.debug('Configuration details:', config);
logger.warn('Potential issue detected');
logger.error('Operation failed:', error);
logger.success('Operation completed successfully');
```

#### File Organization
- Prefer creating new files grouped by functionality over adding to existing files
- Place core logic in `src/`
- Place container configurations in `containers/`
- Place CI/CD scripts in `scripts/ci/`
- Add tests alongside your code (e.g., `feature.ts` and `feature.test.ts`)

### Documentation
- Update documentation for any new features
- Add examples where helpful
- Ensure documentation is clear and concise

### Testing
- Write unit tests for new functionality
- Ensure all tests pass (`npm test`)
- Test manually with Docker containers when possible
- Integration tests require sudo access for iptables

## 🔄 Pull Request Process

1. **Before submitting:**
   - Run `npm run lint` to check code style
   - Run `npm test` to ensure all tests pass
   - Run `npm run build` to verify clean build
   - Test your changes manually
   - Update documentation if needed

2. **Pull request requirements:**
   - Clear description of what the PR does
   - Reference any related issues
   - Include tests for new functionality
   - Ensure CI passes (including test coverage checks)
   - Review the automated coverage report posted as a PR comment

3. **Review process:**
   - Maintainers will review your PR
   - The coverage report bot will automatically comment with test coverage metrics
   - Address any feedback
   - Once approved, your PR will be merged

## 🏗️ Project Structure

```
/
├── src/                     # TypeScript source code
│   ├── cli.ts               # CLI entry point
│   ├── docker-manager.ts    # Docker container management
│   ├── squid-config.ts      # Squid proxy configuration
│   ├── host-iptables.ts     # Host-level iptables management
│   ├── logger.ts            # Logging utilities
│   └── types.ts             # TypeScript type definitions
├── containers/              # Docker container definitions
│   ├── squid/               # Squid proxy container
│   └── agent/               # Agent execution container
├── scripts/                 # Utility scripts
│   └── ci/                  # CI/CD scripts
├── docs/                    # Documentation
├── .github/workflows/       # GitHub Actions CI/CD
├── dist/                    # Built JavaScript (generated)
├── package.json             # npm package configuration
└── tsconfig.json            # TypeScript configuration
```

## 🤝 Community

- Participate in discussions on GitHub issues
- Help other contributors and users

## 📜 Code of Conduct

This project follows the GitHub Community Guidelines. Please be respectful and inclusive in all interactions.

## ❓ Getting Help

- Check the [README.md](README.md) for usage instructions
- Review the [Quick Start Guide](docs/quickstart.md) for setup
- Explore [AGENTS.md](AGENTS.md) for detailed development guidance
- Ask questions in GitHub issues
- Look at existing code and tests for examples

Thank you for contributing to Agentic Workflow Firewall! 🎉<!--

Hello fellow agent! Welcome to GitHub Agentic Workflows = Actions + Agent + Safety. 
Here are some pointers to get you started in using this tool.

- Create a new workflow: https://raw.githubusercontent.com/github/gh-aw/main/create.md
- Install: https://raw.githubusercontent.com/github/gh-aw/main/install.md
- Reference: https://raw.githubusercontent.com/github/gh-aw/main/.github/aw/github-agentic-workflows.md

-->

# GitHub Agentic Workflows

Write agentic workflows in natural language markdown, and run them in GitHub Actions.

## Contents

- [Quick Start](#quick-start)
- [Overview](#overview)
- [Guardrails](#guardrails)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Share Feedback](#share-feedback)
- [Peli's Agent Factory](#pelis-agent-factory)
- [Related Projects](#related-projects)

## Quick Start

Ready to get your first agentic workflow running? Follow our step-by-step [Quick Start Guide](https://github.github.com/gh-aw/setup/quick-start/) to install the extension, add a sample workflow, and see it in action.

## Overview

Learn about the concepts behind agentic workflows, explore available workflow types, and understand how AI can automate your repository tasks. See [How It Works](https://github.github.com/gh-aw/introduction/how-they-work/).

## Guardrails

Guardrails, safety and security are foundational to GitHub Agentic Workflows. Workflows run with read-only permissions by default, with write operations only allowed through sanitized `safe-outputs`. The system implements multiple layers of protection including sandboxed execution, input sanitization, network isolation, supply chain security (SHA-pinned dependencies), tool allow-listing, and compile-time validation. Access can be gated to team members only, with human approval gates for critical operations, ensuring AI agents operate safely within controlled boundaries. See the [Security Architecture](https://github.github.com/gh-aw/introduction/architecture/) for comprehensive details on threat modeling, implementation guidelines, and best practices.

Using agentic workflows in your repository requires careful attention to security considerations and careful human supervision, and even then things can still go wrong. Use it with caution, and at your own risk.

## Documentation

For complete documentation, examples, and guides, see the [Documentation](https://github.github.com/gh-aw/). If you are an agent, download the [llms.txt](https://github.github.com/gh-aw/llms.txt).

## Contributing

For development setup and contribution guidelines, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Share Feedback

We welcome your feedback on GitHub Agentic Workflows! 

- [Community Feedback Discussions](https://github.com/orgs/community/discussions/186451)
- [GitHub Next Discord](https://gh.io/next-discord)

## Peli's Agent FactoryDEBUG=true npm start --workspace @google/gemini-cli
npm install
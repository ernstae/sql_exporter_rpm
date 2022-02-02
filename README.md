# Build Instructions
Prometheus SQL Exporter RPM Build

This work was adapted from  https://packages.credativ.com/public/postgresql/yum/el7-test/src/sql_exporter-0.2.0-1.el7.centos.src.rpm which appears to no longer be maintained by @credativ

Steps to a successful build on CentOS 7

1. Remove git and upgrade to version > 2.x
```
sudo yum install https://packages.endpointdev.com/rhel/7/os/x86_64/endpoint-repo.x86_64.rpm
sudo yum clean all
sudo yum remove git
```

2. Install all the dependency packages
```
yum install epel-release golang go git rpm-build help2man
```

3. Download the .src.rpm and build.
```
[root@buildhost002 SPECS]# rpmbuild -ba sql_exporter.spec
Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.6RDfUd
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd /root/rpmbuild/BUILD
+ rm -rf sql_exporter-0.4.2
+ /usr/bin/gzip -dc /root/rpmbuild/SOURCES/sql_exporter-0.4.2.tar.gz
+ /usr/bin/tar -xf -
+ STATUS=0
+ '[' 0 -ne 0 ']'
+ cd sql_exporter-0.4.2
+ /usr/bin/chmod -Rf a+rX,u+w,g-w,o-w .
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.p7Rxj8
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd sql_exporter-0.4.2
+ go get github.com/justwatchcom/sql_exporter
+ GOPATH=/root/rpmbuild/BUILD/go
+ go get -v github.com/justwatchcom/sql_exporter
get "golang.org/x/net": found meta tag vcs.metaImport{Prefix:"golang.org/x/net", VCS:"git", RepoRoot:"https://go.googlesource.com/net"} at //golang.org/x/net?go-get=1
get "golang.org/x/crypto": found meta tag vcs.metaImport{Prefix:"golang.org/x/crypto", VCS:"git", RepoRoot:"https://go.googlesource.com/crypto"} at //golang.org/x/crypto?go-get=1
get "golang.org/x/sys": found meta tag vcs.metaImport{Prefix:"golang.org/x/sys", VCS:"git", RepoRoot:"https://go.googlesource.com/sys"} at //golang.org/x/sys?go-get=1
get "golang.org/x/xerrors": found meta tag vcs.metaImport{Prefix:"golang.org/x/xerrors", VCS:"git", RepoRoot:"https://go.googlesource.com/xerrors"} at //golang.org/x/xerrors?go-get=1
get "google.golang.org/protobuf": found meta tag vcs.metaImport{Prefix:"google.golang.org/protobuf", VCS:"git", RepoRoot:"https://go.googlesource.com/protobuf"} at //google.golang.org/protobuf?go-get=1
get "gopkg.in/yaml.v2": found meta tag vcs.metaImport{Prefix:"gopkg.in/yaml.v2", VCS:"git", RepoRoot:"https://gopkg.in/yaml.v2"} at //gopkg.in/yaml.v2?go-get=1
+ exit 0
Executing(%install): /bin/sh -e /var/tmp/rpm-tmp.8VVEnK
+ umask 022
+ cd /root/rpmbuild/BUILD
+ '[' /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64 '!=' / ']'
+ rm -rf /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64
++ dirname /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64
+ mkdir -p /root/rpmbuild/BUILDROOT
+ mkdir /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64
+ cd sql_exporter-0.4.2
+ install -m 0755 -d /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/sbin
+ install -m 0755 -D -s /root/rpmbuild/BUILD/go/bin/sql_exporter /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/bin/prometheus-sql-exporter
+ install -m 0644 -D /root/rpmbuild/SOURCES/prometheus-sql-exporter.default /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/etc/default/prometheus-sql-exporter
+ install -m 0644 -D /root/rpmbuild/SOURCES/prometheus-sql-exporter.service /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/lib/systemd/system/prometheus-sql-exporter.service
+ mkdir -p /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/share/man/man1
+ PATH=/root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin
+ help2man --no-discard-stderr --no-info --name 'SQL Exporter for Prometheus' --version-string=0.4.2 prometheus-sql-exporter
+ install -m 0644 -D prometheus-sql-exporter.1 /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/share/man/man1/prometheus-sql-exporter.1
+ /usr/lib/rpm/find-debuginfo.sh --strict-build-id -m --run-dwz --dwz-low-mem-die-limit 10000000 --dwz-max-die-limit 110000000 /root/rpmbuild/BUILD/sql_exporter-0.4.2
/usr/lib/rpm/sepdebugcrcfix: Updated 0 CRC32s, 0 CRC32s did match.
find: 'debug': No such file or directory
+ /usr/lib/rpm/check-buildroot
+ /usr/lib/rpm/redhat/brp-compress
+ /usr/lib/rpm/redhat/brp-strip-static-archive /usr/bin/strip
+ /usr/lib/rpm/brp-python-bytecompile /usr/bin/python 1
+ /usr/lib/rpm/redhat/brp-python-hardlink
+ /usr/lib/rpm/redhat/brp-java-repack-jars
Processing files: sql_exporter-0.4.2-1.el7.x86_64
Executing(%doc): /bin/sh -e /var/tmp/rpm-tmp.rkVFan
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd sql_exporter-0.4.2
+ DOCDIR=/root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/share/doc/sql_exporter-0.4.2
+ export DOCDIR
+ /usr/bin/mkdir -p /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/share/doc/sql_exporter-0.4.2
+ cp -pr LICENSE /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64/usr/share/doc/sql_exporter-0.4.2
+ exit 0
Provides: config(sql_exporter) = 0.4.2-1.el7 sql_exporter = 0.4.2-1.el7 sql_exporter(x86-64) = 0.4.2-1.el7
Requires(rpmlib): rpmlib(CompressedFileNames) <= 3.0.4-1 rpmlib(FileDigests) <= 4.6.0-1 rpmlib(PayloadFilesHavePrefix) <= 4.0-1
Requires(post): systemd
Requires(preun): systemd
Requires(postun): systemd
Requires: libc.so.6()(64bit) libc.so.6(GLIBC_2.2.5)(64bit) libpthread.so.0()(64bit) libpthread.so.0(GLIBC_2.2.5)(64bit) libpthread.so.0(GLIBC_2.3.2)(64bit)
Processing files: sql_exporter-debuginfo-0.4.2-1.el7.x86_64
Provides: sql_exporter-debuginfo = 0.4.2-1.el7 sql_exporter-debuginfo(x86-64) = 0.4.2-1.el7
Requires(rpmlib): rpmlib(FileDigests) <= 4.6.0-1 rpmlib(PayloadFilesHavePrefix) <= 4.0-1 rpmlib(CompressedFileNames) <= 3.0.4-1
Checking for unpackaged file(s): /usr/lib/rpm/check-files /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64
Wrote: /root/rpmbuild/SRPMS/sql_exporter-0.4.2-1.el7.src.rpm
Wrote: /root/rpmbuild/RPMS/x86_64/sql_exporter-0.4.2-1.el7.x86_64.rpm
Wrote: /root/rpmbuild/RPMS/x86_64/sql_exporter-debuginfo-0.4.2-1.el7.x86_64.rpm
Executing(%clean): /bin/sh -e /var/tmp/rpm-tmp.htbkDd
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd sql_exporter-0.4.2
+ /usr/bin/rm -rf /root/rpmbuild/BUILDROOT/sql_exporter-0.4.2-1.el7.x86_64
+ exit 0
```

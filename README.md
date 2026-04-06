**How to build cURL Windows Static Library files for linking in C++**

Extract the cURL source code zip folder and navigate to the CMake folder
C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0>cmake -B "Visual Studio 17 2022" -A x64 -DBUILD_SHARED_LIBS=ON -DCURL_USE_LIBPSL=OFF -DENABLE_UNICODE=ON -DBUILD_STATIC_LIBS=ON

and also below command can be run after the first command runs to success.
cmake -G "Visual Studio 17 2022" -A x64 -DBUILD_SHARED_LIBS=ON -DCURL_USE_LIBPSL=OFF -DENABLE_UNICODE=ON -DBUILD_STATIC_LIBS=ON

Output:

-- Building for: Visual Studio 17 2022
-- Using CMake version 3.22.22040401-MSVC_2
-- curl version=[8.19.0]
-- Selecting Windows SDK version 10.0.19041.0 to target Windows 10.0.19045.
-- The C compiler identification is MSVC 19.32.31332.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.32.31326/bin/Hostx64/x64/cl.exe - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- CMake platform flags: WIN32 MSVC-1932
-- Performing Test HAVE_WIN32_WINNT
-- Performing Test HAVE_WIN32_WINNT - Success
-- Found _WIN32_WINNT=0x0a00
-- Picky compiler options: -W4 -Wall -wd4061 -wd4191 -wd4255 -wd4464 -wd4548 -wd4574 -wd4668 -wd4710 -wd4711 -wd4746 -wd4820 -wd5045
-- Could NOT find Perl (missing: PERL_EXECUTABLE)
CMake Warning at CMakeLists.txt:580 (message):
  Perl not found.  Will not build manuals.


-- Could NOT find ZLIB (missing: ZLIB_LIBRARY ZLIB_INCLUDE_DIR)
-- Could NOT find Brotli (missing: BROTLI_INCLUDE_DIR BROTLIDEC_LIBRARY BROTLICOMMON_LIBRARY)
-- Could NOT find Zstd (missing: ZSTD_INCLUDE_DIR ZSTD_LIBRARY)
-- Could NOT find NGHTTP2 (missing: NGHTTP2_INCLUDE_DIR NGHTTP2_LIBRARY)
-- Could NOT find Libidn2 (missing: LIBIDN2_INCLUDE_DIR LIBIDN2_LIBRARY)
-- Could NOT find Libssh2 (missing: LIBSSH2_INCLUDE_DIR LIBSSH2_LIBRARY)
-- Check size of time_t
-- Check size of time_t - done
-- Perl not found. Using the pre-built tool_hugehelp.c found in the source tree.
-- Protocols: dict file ftp gopher http imap ipfs ipns ldap ldaps mqtt pop3 rtsp smb smtp telnet tftp ws
-- Features: alt-svc AsynchDNS IPv6 Largefile NTLM threadsafe Unicode UnixSockets
-- Enabled SSL backends:
-- Configuring done
-- Generating done
-- Build files have been written to: C:/Users/hp/Downloads/curl-8.19.0/curl-8.19.0/Visual Studio 17 2022

C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0>

Now navigate to the build folder lib as below,
C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0>cd C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib

Now execute the following command: 
msbuild libcurl_static.vcxproj /t:Build /p:Configuration=Release /p:Platform=x64

Microsoft (R) Build Engine version 17.2.1+52cd2da31 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 4/6/2026 2:15:05 PM.
Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_static.vcxproj" on node 1 (Build target(s)).
Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_static.vcxproj" (1) is building "C:\Users\hp\Do
wnloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\ZERO_CHECK.vcxproj" (2) on node 1 (default targets).
PrepareForBuild:
  Creating directory "x64\Release\ZERO_CHECK\".
  Creating directory "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\".
InitializeBuildStatus:
  Creating "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\unsuccessfulbuild" because "AlwaysCreate" was specified.
CustomBuild:
  Checking Build System
FinalizeBuildStatus:
  Deleting file "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\unsuccessfulbuild".
  Touching "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\ZERO_CHECK.lastbuildstate".
Done Building Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\ZERO_CHECK.vcxproj" (default targets).

Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_static.vcxproj" (1) is building "C:\Users\hp\Do
wnloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.vcxproj" (3) on node 1 (default targets).
PrepareForBuild:
  Creating directory "libcurl_object.dir\Release\".
  Creating directory "libcurl_object.dir\Release\libcurl_object.tlog\".
InitializeBuildStatus:
  Creating "libcurl_object.dir\Release\libcurl_object.tlog\unsuccessfulbuild" because "AlwaysCreate" was specified.
CustomBuild:
  Building Custom Rule C:/Users/hp/Downloads/curl-8.19.0/curl-8.19.0/lib/CMakeLists.txt
ClCompile:
  C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.32.31326\bin\HostX64\x64\CL.exe /c /I"C:\Users\hp\Downloads\c
  url-8.19.0\curl-8.19.0\include" /I"C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib" /I"C:\Users\hp\Downloads\c
  url-8.19.0\curl-8.19.0\lib" /nologo /Wall /WX- /diagnostics:column /MP /O2 /Ob2 /D _UNICODE /D UNICODE /D WIN32 /D _WINDOWS /D NDEBUG
  /D CURL_STATICLIB /D CURL_HIDDEN_SYMBOLS /D UNICODE /D _UNICODE /D HAVE_CONFIG_H /D BUILDING_LIBCURL /D "CMAKE_INTDIR=\"Release\"" /Gm
  - /MD /GS /fp:precise /Zc:wchar_t /Zc:forScope /Zc:inline /Fo"libcurl_object.dir\Release\\" /Fd"libcurl_object.dir\Release\libcurl_obj
  ect.pdb" /external:W4 /Gd /TC /wd4061 /wd4191 /wd4255 /wd4464 /wd4548 /wd4574 /wd4668 /wd4710 /wd4711 /wd4746 /wd4820 /wd5045 /errorRe
  port:queue "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\altsvc.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\amigaos.c"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\asyn-ares.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\asyn-base.c" "C:\Us
  ers\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\asyn-thrdd.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\bufq.c" "C:\Users\hp\Dow
  nloads\curl-8.19.0\curl-8.19.0\lib\bufref.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cf-h1-proxy.c" "C:\Users\hp\Downloads\
  curl-8.19.0\curl-8.19.0\lib\cf-h2-proxy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cf-haproxy.c" "C:\Users\hp\Downloads\cur
  l-8.19.0\curl-8.19.0\lib\cf-https-connect.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cf-ip-happy.c" "C:\Users\hp\Downloads\
  curl-8.19.0\curl-8.19.0\lib\cf-socket.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cfilters.c" "C:\Users\hp\Downloads\curl-8.
  19.0\curl-8.19.0\lib\conncache.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\connect.c" "C:\Users\hp\Downloads\curl-8.19.0\cur
  l-8.19.0\lib\content_encoding.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cookie.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-
  8.19.0\lib\cshutdn.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_addrinfo.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19
  .0\lib\curl_endian.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_fnmatch.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.
  0\lib\curl_fopen.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_get_line.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0
  \lib\curl_gethostname.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_gssapi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.1
  9.0\lib\curl_memrchr.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_ntlm_core.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8
  .19.0\lib\curl_range.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_rtmp.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0
  \lib\curl_sasl.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_sha512_256.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0
  \lib\curl_share.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_sspi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\
  curl_threads.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curl_trc.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cw-o
  ut.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\cw-pause.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\dict.c" "C:\Us
  ers\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\doh.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\dynhds.c" "C:\Users\hp\Download
  s\curl-8.19.0\curl-8.19.0\lib\easy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\easygetopt.c" "C:\Users\hp\Downloads\curl-8.1
  9.0\curl-8.19.0\lib\easyoptions.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\escape.c" "C:\Users\hp\Downloads\curl-8.19.0\cur
  l-8.19.0\lib\fake_addrinfo.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\file.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.
  0\lib\fileinfo.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\formdata.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\ft
  p.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\ftplistparser.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\getenv.c"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\getinfo.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\gopher.c" "C:\Users\h
  p\Downloads\curl-8.19.0\curl-8.19.0\lib\hash.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\headers.c" "C:\Users\hp\Downloads\c
  url-8.19.0\curl-8.19.0\lib\hmac.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\hostip.c" "C:\Users\hp\Downloads\curl-8.19.0\cur
  l-8.19.0\lib\hostip4.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\hostip6.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\l
  ib\hsts.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http1.c" "C:\
  Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http2.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http_aws_sigv4.c" "C:\Users
  \hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http_chunks.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http_digest.c" "C:\Users\h
  p\Downloads\curl-8.19.0\curl-8.19.0\lib\http_negotiate.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\http_ntlm.c" "C:\Users\hp
  \Downloads\curl-8.19.0\curl-8.19.0\lib\http_proxy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\httpsrr.c" "C:\Users\hp\Downlo
  ads\curl-8.19.0\curl-8.19.0\lib\idn.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\if2ip.c" "C:\Users\hp\Downloads\curl-8.19.0\
  curl-8.19.0\lib\imap.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\ldap.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\
  llist.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\macos.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\md4.c" "C:\Use
  rs\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\md5.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\memdebug.c" "C:\Users\hp\Downloa
  ds\curl-8.19.0\curl-8.19.0\lib\mime.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\mprintf.c" "C:\Users\hp\Downloads\curl-8.19.
  0\curl-8.19.0\lib\mqtt.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\multi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\l
  ib\multi_ev.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\multi_ntfy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\net
  rc.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\noproxy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\openldap.c" "C:
  \Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\parsedate.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\pingpong.c" "C:\Users\
  hp\Downloads\curl-8.19.0\curl-8.19.0\lib\pop3.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\progress.c" "C:\Users\hp\Downloads
  \curl-8.19.0\curl-8.19.0\lib\psl.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\rand.c" "C:\Users\hp\Downloads\curl-8.19.0\curl
  -8.19.0\lib\ratelimit.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\request.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\
  lib\rtsp.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\select.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\sendf.c" "
  C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\setopt.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\sha256.c" "C:\Users\hp\
  Downloads\curl-8.19.0\curl-8.19.0\lib\slist.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\smb.c" "C:\Users\hp\Downloads\curl-8
  .19.0\curl-8.19.0\lib\smtp.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\socketpair.c" "C:\Users\hp\Downloads\curl-8.19.0\curl
  -8.19.0\lib\socks.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\socks_gssapi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0
  \lib\socks_sspi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\splay.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\strc
  ase.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\strequal.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\strerror.c" "
  C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\system_win32.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\telnet.c" "C:\Use
  rs\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\tftp.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\transfer.c" "C:\Users\hp\Downlo
  ads\curl-8.19.0\curl-8.19.0\lib\uint-bset.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\uint-hash.c" "C:\Users\hp\Downloads\cu
  rl-8.19.0\curl-8.19.0\lib\uint-spbset.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\uint-table.c" "C:\Users\hp\Downloads\curl-
  8.19.0\curl-8.19.0\lib\url.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\urlapi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.1
  9.0\lib\version.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\ws.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\c
  leartext.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\cram.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\
  digest.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\digest_sspi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\v
  auth\gsasl.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\krb5_gssapi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\l
  ib\vauth\krb5_sspi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\ntlm.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\
  lib\vauth\ntlm_sspi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\oauth2.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19
  .0\lib\vauth\spnego_gssapi.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vauth\spnego_sspi.c" "C:\Users\hp\Downloads\curl-8.19
  .0\curl-8.19.0\lib\vauth\vauth.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\apple.c" "C:\Users\hp\Downloads\curl-8.19.0\
  curl-8.19.0\lib\vtls\cipher_suite.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\gtls.c" "C:\Users\hp\Downloads\curl-8.19.
  0\curl-8.19.0\lib\vtls\hostcheck.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\keylog.c" "C:\Users\hp\Downloads\curl-8.19
  .0\curl-8.19.0\lib\vtls\mbedtls.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\openssl.c" "C:\Users\hp\Downloads\curl-8.19
  .0\curl-8.19.0\lib\vtls\rustls.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\schannel.c" "C:\Users\hp\Downloads\curl-8.19
  .0\curl-8.19.0\lib\vtls\schannel_verify.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\vtls.c" "C:\Users\hp\Downloads\curl
  -8.19.0\curl-8.19.0\lib\vtls\vtls_scache.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\vtls_spack.c" "C:\Users\hp\Downloa
  ds\curl-8.19.0\curl-8.19.0\lib\vtls\wolfssl.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vtls\x509asn1.c" "C:\Users\hp\Downlo
  ads\curl-8.19.0\curl-8.19.0\lib\vquic\curl_ngtcp2.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vquic\curl_quiche.c" "C:\Users
  \hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vquic\vquic.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vquic\vquic-tls.c" "C:\Use
  rs\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vssh\libssh.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vssh\libssh2.c" "C:\User
  s\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\vssh\vssh.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\base64.c" "C:\Users\h
  p\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\basename.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\dynbuf.c" "C:\Users
  \hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\fopen.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\inet_ntop.c" "C:\Use
  rs\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\inet_pton.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\multibyte.c" "
  C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\nonblock.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\snprintf.
  c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\strcopy.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\strdup
  .c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\strerr.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\strpar
  se.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\timediff.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\ti
  meval.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\version_win32.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\
  curlx\wait.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\curlx\warnless.c" "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\lib\
  curlx\winapi.c"
  altsvc.c
  amigaos.c
  asyn-ares.c
  asyn-base.c
  asyn-thrdd.c
  bufq.c
  bufref.c
  cf-h1-proxy.c
  cf-h2-proxy.c
  cf-haproxy.c
  cf-https-connect.c
  cf-ip-happy.c
  cf-socket.c
  cfilters.c
  conncache.c
  connect.c
  content_encoding.c
  cookie.c
  cshutdn.c
  curl_addrinfo.c
  curl_endian.c
  curl_fnmatch.c
  curl_fopen.c
  curl_get_line.c
  curl_gethostname.c
  curl_gssapi.c
  curl_memrchr.c
  curl_ntlm_core.c
  curl_range.c
  curl_rtmp.c
  curl_sasl.c
  curl_sha512_256.c
  curl_share.c
  curl_sspi.c
  curl_threads.c
  curl_trc.c
  cw-out.c
  cw-pause.c
  dict.c
  doh.c
  dynhds.c
  easy.c
  easygetopt.c
  easyoptions.c
  escape.c
  fake_addrinfo.c
  file.c
  fileinfo.c
  formdata.c
  ftp.c
  ftplistparser.c
  getenv.c
  getinfo.c
  gopher.c
  hash.c
  headers.c
  hmac.c
  hostip.c
  hostip4.c
  hostip6.c
  hsts.c
  http.c
  http1.c
  http2.c
  http_aws_sigv4.c
  http_chunks.c
  http_digest.c
  http_negotiate.c
  http_ntlm.c
  http_proxy.c
  httpsrr.c
  idn.c
  if2ip.c
  imap.c
  ldap.c
  llist.c
  macos.c
  md4.c
  md5.c
  memdebug.c
  mime.c
  mprintf.c
  mqtt.c
  multi.c
  multi_ev.c
  multi_ntfy.c
  netrc.c
  noproxy.c
  openldap.c
  parsedate.c
  pingpong.c
  pop3.c
  progress.c
  psl.c
  rand.c
  ratelimit.c
  request.c
  rtsp.c
  select.c
  sendf.c
  setopt.c
  sha256.c
  slist.c
  smb.c
  smtp.c
  socketpair.c
  socks.c
  socks_gssapi.c
  socks_sspi.c
  splay.c
  strcase.c
  strequal.c
  strerror.c
  system_win32.c
  telnet.c
  tftp.c
  transfer.c
  uint-bset.c
  uint-hash.c
  uint-spbset.c
  uint-table.c
  url.c
  urlapi.c
  version.c
  ws.c
  cleartext.c
  cram.c
  digest.c
  digest_sspi.c
  gsasl.c
  krb5_gssapi.c
  krb5_sspi.c
  ntlm.c
  ntlm_sspi.c
  oauth2.c
  spnego_gssapi.c
  spnego_sspi.c
  vauth.c
  apple.c
  cipher_suite.c
  gtls.c
  hostcheck.c
  keylog.c
  mbedtls.c
  openssl.c
  rustls.c
  schannel.c
  schannel_verify.c
  vtls.c
  vtls_scache.c
  vtls_spack.c
  wolfssl.c
  x509asn1.c
  curl_ngtcp2.c
  curl_quiche.c
  vquic.c
  vquic-tls.c
  libssh.c
  libssh2.c
  vssh.c
  base64.c
  basename.c
  dynbuf.c
  fopen.c
  inet_ntop.c
  inet_pton.c
  multibyte.c
  nonblock.c
  snprintf.c
  strcopy.c
  strdup.c
  strerr.c
  strparse.c
  timediff.c
  timeval.c
  version_win32.c
  wait.c
  warnless.c
  winapi.c
Lib:
  C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.32.31326\bin\HostX64\x64\Lib.exe /OUT:"libcurl_object.dir\Rel
  ease\libcurl_object.lib" /NOLOGO /MACHINE:X64  /machine:x64 libcurl_object.dir\Release\altsvc.obj
  libcurl_object.dir\Release\amigaos.obj
  "libcurl_object.dir\Release\asyn-ares.obj"
  "libcurl_object.dir\Release\asyn-base.obj"
  "libcurl_object.dir\Release\asyn-thrdd.obj"
  libcurl_object.dir\Release\bufq.obj
  libcurl_object.dir\Release\bufref.obj
  "libcurl_object.dir\Release\cf-h1-proxy.obj"
  "libcurl_object.dir\Release\cf-h2-proxy.obj"
  "libcurl_object.dir\Release\cf-haproxy.obj"
  "libcurl_object.dir\Release\cf-https-connect.obj"
  "libcurl_object.dir\Release\cf-ip-happy.obj"
  "libcurl_object.dir\Release\cf-socket.obj"
  libcurl_object.dir\Release\cfilters.obj
  libcurl_object.dir\Release\conncache.obj
  libcurl_object.dir\Release\connect.obj
  libcurl_object.dir\Release\content_encoding.obj
  libcurl_object.dir\Release\cookie.obj
  libcurl_object.dir\Release\cshutdn.obj
  libcurl_object.dir\Release\curl_addrinfo.obj
  libcurl_object.dir\Release\curl_endian.obj
  libcurl_object.dir\Release\curl_fnmatch.obj
  libcurl_object.dir\Release\curl_fopen.obj
  libcurl_object.dir\Release\curl_get_line.obj
  libcurl_object.dir\Release\curl_gethostname.obj
  libcurl_object.dir\Release\curl_gssapi.obj
  libcurl_object.dir\Release\curl_memrchr.obj
  libcurl_object.dir\Release\curl_ntlm_core.obj
  libcurl_object.dir\Release\curl_range.obj
  libcurl_object.dir\Release\curl_rtmp.obj
  libcurl_object.dir\Release\curl_sasl.obj
  libcurl_object.dir\Release\curl_sha512_256.obj
  libcurl_object.dir\Release\curl_share.obj
  libcurl_object.dir\Release\curl_sspi.obj
  libcurl_object.dir\Release\curl_threads.obj
  libcurl_object.dir\Release\curl_trc.obj
  "libcurl_object.dir\Release\cw-out.obj"
  "libcurl_object.dir\Release\cw-pause.obj"
  libcurl_object.dir\Release\dict.obj
  libcurl_object.dir\Release\doh.obj
  libcurl_object.dir\Release\dynhds.obj
  libcurl_object.dir\Release\easy.obj
  libcurl_object.dir\Release\easygetopt.obj
  libcurl_object.dir\Release\easyoptions.obj
  libcurl_object.dir\Release\escape.obj
  libcurl_object.dir\Release\fake_addrinfo.obj
  libcurl_object.dir\Release\file.obj
  libcurl_object.dir\Release\fileinfo.obj
  libcurl_object.dir\Release\formdata.obj
  libcurl_object.dir\Release\ftp.obj
  libcurl_object.dir\Release\ftplistparser.obj
  libcurl_object.dir\Release\getenv.obj
  libcurl_object.dir\Release\getinfo.obj
  libcurl_object.dir\Release\gopher.obj
  libcurl_object.dir\Release\hash.obj
  libcurl_object.dir\Release\headers.obj
  libcurl_object.dir\Release\hmac.obj
  libcurl_object.dir\Release\hostip.obj
  libcurl_object.dir\Release\hostip4.obj
  libcurl_object.dir\Release\hostip6.obj
  libcurl_object.dir\Release\hsts.obj
  libcurl_object.dir\Release\http.obj
  libcurl_object.dir\Release\http1.obj
  libcurl_object.dir\Release\http2.obj
  libcurl_object.dir\Release\http_aws_sigv4.obj
  libcurl_object.dir\Release\http_chunks.obj
  libcurl_object.dir\Release\http_digest.obj
  libcurl_object.dir\Release\http_negotiate.obj
  libcurl_object.dir\Release\http_ntlm.obj
  libcurl_object.dir\Release\http_proxy.obj
  libcurl_object.dir\Release\httpsrr.obj
  libcurl_object.dir\Release\idn.obj
  libcurl_object.dir\Release\if2ip.obj
  libcurl_object.dir\Release\imap.obj
  libcurl_object.dir\Release\ldap.obj
  libcurl_object.dir\Release\llist.obj
  libcurl_object.dir\Release\macos.obj
  libcurl_object.dir\Release\md4.obj
  libcurl_object.dir\Release\md5.obj
  libcurl_object.dir\Release\memdebug.obj
  libcurl_object.dir\Release\mime.obj
  libcurl_object.dir\Release\mprintf.obj
  libcurl_object.dir\Release\mqtt.obj
  libcurl_object.dir\Release\multi.obj
  libcurl_object.dir\Release\multi_ev.obj
  libcurl_object.dir\Release\multi_ntfy.obj
  libcurl_object.dir\Release\netrc.obj
  libcurl_object.dir\Release\noproxy.obj
  libcurl_object.dir\Release\openldap.obj
  libcurl_object.dir\Release\parsedate.obj
  libcurl_object.dir\Release\pingpong.obj
  libcurl_object.dir\Release\pop3.obj
  libcurl_object.dir\Release\progress.obj
  libcurl_object.dir\Release\psl.obj
  libcurl_object.dir\Release\rand.obj
  libcurl_object.dir\Release\ratelimit.obj
  libcurl_object.dir\Release\request.obj
  libcurl_object.dir\Release\rtsp.obj
  libcurl_object.dir\Release\select.obj
  libcurl_object.dir\Release\sendf.obj
  libcurl_object.dir\Release\setopt.obj
  libcurl_object.dir\Release\sha256.obj
  libcurl_object.dir\Release\slist.obj
  libcurl_object.dir\Release\smb.obj
  libcurl_object.dir\Release\smtp.obj
  libcurl_object.dir\Release\socketpair.obj
  libcurl_object.dir\Release\socks.obj
  libcurl_object.dir\Release\socks_gssapi.obj
  libcurl_object.dir\Release\socks_sspi.obj
  libcurl_object.dir\Release\splay.obj
  libcurl_object.dir\Release\strcase.obj
  libcurl_object.dir\Release\strequal.obj
  libcurl_object.dir\Release\strerror.obj
  libcurl_object.dir\Release\system_win32.obj
  libcurl_object.dir\Release\telnet.obj
  libcurl_object.dir\Release\tftp.obj
  libcurl_object.dir\Release\transfer.obj
  "libcurl_object.dir\Release\uint-bset.obj"
  "libcurl_object.dir\Release\uint-hash.obj"
  "libcurl_object.dir\Release\uint-spbset.obj"
  "libcurl_object.dir\Release\uint-table.obj"
  libcurl_object.dir\Release\url.obj
  libcurl_object.dir\Release\urlapi.obj
  libcurl_object.dir\Release\version.obj
  libcurl_object.dir\Release\ws.obj
  libcurl_object.dir\Release\cleartext.obj
  libcurl_object.dir\Release\cram.obj
  libcurl_object.dir\Release\digest.obj
  libcurl_object.dir\Release\digest_sspi.obj
  libcurl_object.dir\Release\gsasl.obj
  libcurl_object.dir\Release\krb5_gssapi.obj
  libcurl_object.dir\Release\krb5_sspi.obj
  libcurl_object.dir\Release\ntlm.obj
  libcurl_object.dir\Release\ntlm_sspi.obj
  libcurl_object.dir\Release\oauth2.obj
  libcurl_object.dir\Release\spnego_gssapi.obj
  libcurl_object.dir\Release\spnego_sspi.obj
  libcurl_object.dir\Release\vauth.obj
  libcurl_object.dir\Release\apple.obj
  libcurl_object.dir\Release\cipher_suite.obj
  libcurl_object.dir\Release\gtls.obj
  libcurl_object.dir\Release\hostcheck.obj
  libcurl_object.dir\Release\keylog.obj
  libcurl_object.dir\Release\mbedtls.obj
  libcurl_object.dir\Release\openssl.obj
  libcurl_object.dir\Release\rustls.obj
  libcurl_object.dir\Release\schannel.obj
  libcurl_object.dir\Release\schannel_verify.obj
  libcurl_object.dir\Release\vtls.obj
  libcurl_object.dir\Release\vtls_scache.obj
  libcurl_object.dir\Release\vtls_spack.obj
  libcurl_object.dir\Release\wolfssl.obj
  libcurl_object.dir\Release\x509asn1.obj
  libcurl_object.dir\Release\curl_ngtcp2.obj
  libcurl_object.dir\Release\curl_quiche.obj
  libcurl_object.dir\Release\vquic.obj
  "libcurl_object.dir\Release\vquic-tls.obj"
  libcurl_object.dir\Release\libssh.obj
  libcurl_object.dir\Release\libssh2.obj
  libcurl_object.dir\Release\vssh.obj
  libcurl_object.dir\Release\base64.obj
  libcurl_object.dir\Release\basename.obj
  libcurl_object.dir\Release\dynbuf.obj
  libcurl_object.dir\Release\fopen.obj
  libcurl_object.dir\Release\inet_ntop.obj
  libcurl_object.dir\Release\inet_pton.obj
  libcurl_object.dir\Release\multibyte.obj
  libcurl_object.dir\Release\nonblock.obj
  libcurl_object.dir\Release\snprintf.obj
  libcurl_object.dir\Release\strcopy.obj
  libcurl_object.dir\Release\strdup.obj
  libcurl_object.dir\Release\strerr.obj
  libcurl_object.dir\Release\strparse.obj
  libcurl_object.dir\Release\timediff.obj
  libcurl_object.dir\Release\timeval.obj
  libcurl_object.dir\Release\version_win32.obj
  libcurl_object.dir\Release\wait.obj
  libcurl_object.dir\Release\warnless.obj
  libcurl_object.dir\Release\winapi.obj
  libcurl_object.vcxproj -> C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\libcurl_o
  bject.lib
FinalizeBuildStatus:
  Deleting file "libcurl_object.dir\Release\libcurl_object.tlog\unsuccessfulbuild".
  Touching "libcurl_object.dir\Release\libcurl_object.tlog\libcurl_object.lastbuildstate".
Done Building Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.vcxproj" (default targets)
.

PrepareForBuild:
  Creating directory "libcurl_static.dir\Release\".
  Creating directory "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\Release\".
  Creating directory "libcurl_static.dir\Release\libcurl_static.tlog\".
InitializeBuildStatus:
  Creating "libcurl_static.dir\Release\libcurl_static.tlog\unsuccessfulbuild" because "AlwaysCreate" was specified.
CustomBuild:
  Building Custom Rule C:/Users/hp/Downloads/curl-8.19.0/curl-8.19.0/lib/CMakeLists.txt
Lib:
  C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.32.31326\bin\HostX64\x64\Lib.exe /OUT:"C:\Users\hp\Downloads\
  curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\Release\libcurl.lib" /NOLOGO /MACHINE:X64  /machine:x64 "C:\Users\hp\Downloads\curl-
  8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\altsvc.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\amigaos.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\asyn-ares.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\asyn-base.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\asyn-thrdd.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\bufq.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\bufref.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-h1-proxy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-h2-proxy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-haproxy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-https-connect.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-ip-happy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cf-socket.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cfilters.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\conncache.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\connect.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\content_encoding.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cookie.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cshutdn.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_addrinfo.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_endian.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_fnmatch.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_fopen.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_get_line.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_gethostname.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_gssapi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_memrchr.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_ntlm_core.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_range.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_rtmp.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_sasl.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_sha512_256.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_share.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_threads.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_trc.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cw-out.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cw-pause.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\dict.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\doh.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\dynhds.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\easy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\easygetopt.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\easyoptions.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\escape.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\fake_addrinfo.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\file.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\fileinfo.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\formdata.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ftp.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ftplistparser.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\getenv.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\getinfo.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\gopher.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hash.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\headers.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hmac.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hostip.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hostip4.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hostip6.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hsts.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http1.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http2.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_aws_sigv4.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_chunks.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_digest.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_negotiate.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_ntlm.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\http_proxy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\httpsrr.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\idn.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\if2ip.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\imap.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ldap.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\llist.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\macos.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\md4.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\md5.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\memdebug.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\mime.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\mprintf.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\mqtt.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\multi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\multi_ev.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\multi_ntfy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\netrc.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\noproxy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\openldap.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\parsedate.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\pingpong.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\pop3.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\progress.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\psl.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\rand.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ratelimit.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\request.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\rtsp.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\select.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\sendf.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\setopt.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\sha256.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\slist.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\smb.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\smtp.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\socketpair.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\socks.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\socks_gssapi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\socks_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\splay.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strcase.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strequal.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strerror.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\system_win32.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\telnet.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\tftp.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\transfer.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\uint-bset.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\uint-hash.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\uint-spbset.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\uint-table.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\url.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\urlapi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\version.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ws.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cleartext.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cram.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\digest.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\digest_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\gsasl.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\krb5_gssapi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\krb5_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ntlm.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\ntlm_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\oauth2.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\spnego_gssapi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\spnego_sspi.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vauth.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\apple.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\cipher_suite.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\gtls.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\hostcheck.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\keylog.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\mbedtls.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\openssl.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\rustls.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\schannel.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\schannel_verify.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vtls.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vtls_scache.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vtls_spack.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\wolfssl.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\x509asn1.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_ngtcp2.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\curl_quiche.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vquic.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vquic-tls.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\libssh.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\libssh2.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\vssh.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\base64.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\basename.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\dynbuf.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\fopen.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\inet_ntop.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\inet_pton.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\multibyte.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\nonblock.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\snprintf.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strcopy.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strdup.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strerr.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\strparse.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\timediff.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\timeval.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\version_win32.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\wait.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\warnless.obj"
  "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\winapi.obj"
  libcurl_static.vcxproj -> C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\Release\libcurl.lib
FinalizeBuildStatus:
  Deleting file "libcurl_static.dir\Release\libcurl_static.tlog\unsuccessfulbuild".
  Touching "libcurl_static.dir\Release\libcurl_static.tlog\libcurl_static.lastbuildstate".
Done Building Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_static.vcxproj" (Build target(s))
.


Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:28.22

C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib>

The Libcurl.lib file will be placed in the Release folder : C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\Release

now run the following command to get the libcurl_imp.lib file.

msbuild libcurl_shared.vcxproj /t:Build /p:Configuration=Release /p:Platform=x64


C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib>msbuild libcurl_object.vcxproj /t:Build /p:Configuration=Release /p:Platform=x64
Microsoft (R) Build Engine version 17.2.1+52cd2da31 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 4/6/2026 2:31:37 PM.
Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.vcxproj" on node 1 (Build target(s)).
Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.vcxproj" (1) is building "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\V
isual Studio 17 2022\ZERO_CHECK.vcxproj" (2) on node 1 (default targets).
InitializeBuildStatus:
  Creating "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\unsuccessfulbuild" because "AlwaysCreate" was specified.
CustomBuild:
  All outputs are up-to-date.
FinalizeBuildStatus:
  Deleting file "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\unsuccessfulbuild".
  Touching "x64\Release\ZERO_CHECK\ZERO_CHECK.tlog\ZERO_CHECK.lastbuildstate".
Done Building Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\ZERO_CHECK.vcxproj" (default targets).

InitializeBuildStatus:
  Creating "libcurl_object.dir\Release\libcurl_object.tlog\unsuccessfulbuild" because "AlwaysCreate" was specified.
CustomBuild:
  All outputs are up-to-date.
ClCompile:
  All outputs are up-to-date.
Lib:
  All outputs are up-to-date.
  libcurl_object.vcxproj -> C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.dir\Release\libcurl_object.lib
FinalizeBuildStatus:
  Deleting file "libcurl_object.dir\Release\libcurl_object.tlog\unsuccessfulbuild".
  Touching "libcurl_object.dir\Release\libcurl_object.tlog\libcurl_object.lastbuildstate".
Done Building Project "C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib\libcurl_object.vcxproj" (Build target(s)).


Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:00.98

C:\Users\hp\Downloads\curl-8.19.0\curl-8.19.0\Visual Studio 17 2022\lib>

now run the following command to get the libcurl_object.lib file.



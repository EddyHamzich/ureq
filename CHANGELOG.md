# 1.5.5
 * Bugfix: don't reuse conns with bytes pending from server (#372). This
   reduces Transport errors when using an Agent for connection pooling.

# 1.5.4

 * Fix panic introduced in 1.5.4 on redirects. (#274)

# 1.5.3

 * Backport: follow redirects non-body request on 307/308 (#253)

# 1.5.2

 * Remove 'static constraint on Request.send(), allowing a wider variety of
   types to be passed. Also eliminate some copying. (#205).
 * Allow turning a Response into an Error (#214).
 * Update env_logger to 0.8.1 (#195).
 * Remove convenience method for CONNECT verb (#177).
 * Fix bugs in handling of timeout_read (#197 and #198).

# 1.5.1

 * Use cookie_store crate for correct cookie handling (#169).
 * Fix bug in picking wrong host for redirects introduced in 1.5.0 (#180).
 * Allow proxy settings on Agent (#178).

# 1.5.0

 * Add pluggable name resolution. Users can now override the IP addresses for
   hostnames of their choice (#148).
 * bugfix: Don't re-pool streams on drop. This would occur if the user called
   `response.into_reader()` and dropped the resulting `Read` before reading all
   the way to EOF. The result would be a BadStatus error on the next request to
   the same hostname. This only affected users using an explicit Agent (#160).
 * Automatically set Transfer-Encoding: chunked when using `send` (#86).
 * `into_reader()` now returns `impl Read + Send` instead of `impl Read` (#156).
 * Add support for log crate (#170).
 * Retry broken connections in more cases (should reduce BadStatus errors; #168).

# 1.4.1

 * Use buffer to avoid byte-by-byte parsing result in multiple syscalls.
 * Allow pooling multiple connections per host.
 * Put version in user agent "ureq/1.4.1".

# 1.4.0

  * Propagate WouldBlock in io:Error for Response::to_json.
  * Merge multiple cookies into one header to be spec compliant.
  * Allow setting TLSConnector for native-tls.
  * Remove brackets against TLS lib when IPv6 addr is used as hostname.
  * Include proxy in connection pool keys.
  * Stop assuming localhost for URLs without host part.
  * Error if body length is less than content-length.
  * Validate header names.

# 1.3.0

  * Changelog start

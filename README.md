# webserv

![screenshot](/screenshot.png)

**webserv** is an asynchronous HTTP/1.1 web server implemented in C++98, developed as part of the 42Seoul curriculum. The project benchmarks certain features and configuration styles of Nginx, but all core functionality is implemented from scratch. It covers socket programming, I/O multiplexing, HTTP request parsing, CGI handling, and more.

---

## Features

* **Asynchronous I/O:** Efficiently handles multiple client connections using `kqueue`.
* **HTTP/1.1 support:** Implements core HTTP methods (GET, POST, DELETE) and full request parsing.
* **CGI support:** Executes external programs to generate dynamic content, with environment variable setup and pipe management.
* **Config file parsing:** Parses Nginx-style configuration files for flexible server behavior.
* **Cookie and session support:** Supports state management using cookies and sessions.
* **Custom error pages and redirection:** Allows custom error pages and URL redirection.

---

## Project Structure

```
webserv/
├── config/             # Configuration files
├── cgi_bin/            # CGI scripts
├── data/               # Static resources
├── error/              # Error pages
├── source/             # Server source code
├── 42_tester/          # Test scripts and tools
├── Makefile            # Build script
├── leaks_check.sh      # Memory leak check script
├── spacex_test.sh      # Load test script
└── README.md           # Project documentation
```

---

## Build & Run

### 1. Build

```bash
make
```

### 2. Run

```bash
./webserv [path_to_config]
```

* If no config file is provided, the default configuration will be used.
* Example configuration files can be found in the `config/` directory.

---

## Example Configuration

```nginx
server {
    listen 8080;
    server_name localhost;
    root ./data;
    index index.html;

    location / {
        allow_methods GET POST DELETE;
        autoindex on;
    }

    location /cgi-bin/ {
        cgi_pass ./cgi_bin/script.py;
    }

    error_page 404 /error/404.html;
}
```

---

## Testing & Benchmarking

* Use the scripts in the `42_tester/` directory for automated testing.
* For load testing, use `spacex_test.sh`.

---

## Development Period

* November 22, 2022 – January 18, 2023

---

## References

* [HTTP/1.1 RFC 2616](https://www.rfc-editor.org/rfc/rfc2616)
* [Nginx Documentation](https://nginx.org/en/docs/)

---

## Authors

* [Yonaim](https://github.com/Yonaim)
* [earthicko](https://github.com/earthicko)
* [gitubanana](https://github.com/gitubanana)
* [hyeuu](https://github.com/hey-uu)

---

## License

Distributed under the MIT License. See the `LICENSE` file for details.


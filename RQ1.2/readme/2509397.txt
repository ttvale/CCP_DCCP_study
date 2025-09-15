go-httplistd
===

What is it?
---
A simple and (imo) nice-looking HTTP server that lists and serves files and folders. Makes use of Go's `net/http` package.

Install
---
	$ gomake

Make sure you have the Go weekly build (whenever they introduced the `error` built-in type and that stuff). It won't compile otherwise.

Use
---
	$ httplistd -help
	Usage of httplistd:
	  -listen="8080": Port to listen on
	  -root="/moshee": Base path to serve files from '/'
The base path given by the `-root` option must be an absolute path if you use the equals sign (`-root=/home/user/sites/public`). If you must use shorthand, use a space (`-root ~/sites/public`). It defaults to your home directory.

Until I figure out how to fork into the background, run httplistd with screen (`screen -S listd ./httplistd [OPTIONS]`) or jobs (`./httplistd [OPTIONS] &>/dev/null &`).

For now, it's a standalone executable. In the near future I will probably make a package version for my upcoming plugin-oriented web server, `gas`.

Suggestions, comments
---
Contact moshee on Freenode or Rizon.

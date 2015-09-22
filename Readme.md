# Go for Visual Studio Code

This Code extension adds rich language support for the Go language, including:

- Colorization
- Completions Lists (using `gocode`)
- Snippets
- Quick Info (using `godef`)
- Goto Definition (using `godef`)
- Find References (using `go-find-references`)
- Rename (using `gorename`)
- Build-on-save (using `go build` and `go test`)
- Format (using `goreturns` or `goimports` or `gofmt`)
- [partially implemented] Debugging (using `delve`)

## Using

Clone this repo into your Code extensions folder and run `npm install`.

```bash
cd ~/.vscode/extensions/
git clone https://monacotools.visualstudio.com/DefaultCollection/Monaco/_git/go-code
cd go-code
npm install
```

In a terminal window with the GOPATH environment variable set to the GOPATH you want to work on, launch `code`.  Open you GOPATH folder or any subfolder you want to work on, then open a `.go` file to start editing.

### _Optional_: Debugging

To use the debugger, you must currently manually install `delve`.  See the [Installation Instructions](https://github.com/derekparker/delve/wiki/Building) for full details.  This is not support right now on Windows, and on OS X it requires creatinga  self-signed cert to sign the `dlv` binary with.

Once this is installed, go to the Code debug viewlet and select the configuration gear, placing the following in your launch.json:

```json
{
	"version": "0.1.0",
	"configurations": [
		{
			"name": "Delve test",
			"type": "go",
			"program": "/Users/lukeh/dd/go/src/github.com/lukehoban/azuretest/test.go"
		}
	]
}
```

## Building & Running

You can set up a development environment for debugging the extension uring extension development.

First make sure you do not have the extension installed in `~/.vscode/extensions`.  Then clone the repo somewhere else on your machine, and run `npm install` and open a development instance of Code.

```bash
rm -rf ~/.vscode/extensions/go-code
cd ~
https://monacotools.visualstudio.com/DefaultCollection/Monaco/_git/go-code
cd go-code
npm install
code . 
```

To build, use the `Tasks: Run Build Task` command (cmd-shift-B).

To debug, go to the Debug viewlet and select `Launch Extension` then hit play (F5).

In the `[Extension Development Host]` instance, open your GOPATH folder, then close and re-run the `Launch Extension` debug target to attach to launch and attach to an instance of Code opened to your GOAPTH.

You can now hit breakpoints and step through the extension.

## Tools

The extension uses the following tools, installed in the current GOPATH.  If any tools are missing, the extension will offer to install them for you.

- gorename: `go get golang.org/x/tools/cmd/gorename`
- gocode: `go get -u github.com/nsf/gocode`
- goreturns: `go get -u sourcegraph.com/sqs/goreturns`
- godef: `go get -v github.com/rogpeppe/godef`
- golint: `go get -u github.com/golang/lint/golint`
- go-find-references: `go get -v github.com/redefiance/go-find-references`

## Demos

### IDE Features
![IDE](http://i.giphy.com/3oEduO9Rx6awkds4es.gif)

### Debugger
![IDE](http://i.giphy.com/xTiTndDHV3GeIy6aNa.gif)

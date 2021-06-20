# YamYams

Replace Kubernetes YAML with raw Go!

Say so long 👋 to YAML and start using the Go 🎉 programming language.

Take advantage of all the lovely features of Go.

Test your code directly in local Kubernetes using [kind](https://github.com/kubernetes-sigs/kind).

## About

This is a framework for infrastructure teams who need more than just conditional manifests.

Feel free to fork this repository and begin using it for your team. There isn't anything special here. 🤷‍♀ We use the same client the rest of Kubernetes does.

 ❎ No new tools.

 ❎ No learning curve.

 ❎ No barrier to entry.

 ❎ No templating.

 ❎ No vague error messages.

 ✅ Just plain Go.

## Features

✨ There is not a single `.yaml` file in this entire repository. ✨

 - Express applications in 🎉 Go instead of YAML.
 - Use the Go compiler to check your syntax.
 - Write **real tests** 🤓 using Go to check and validate your deployments.
 - Actually test your applications in Kubernetes using [kind](https://github.com/kubernetes-sigs/kind).
 - Define custom installation logic. What happens if it fails?
 - Define custom application registries. Multiple apps of the same flavor? No problem.
 - Use the latest client (the same client the rest of Kubernetes uses).

## Creating a new app 

Copy `sampleapp` to a new folder in `/apps` to get started.

```bash 
cp -rv apps/sampleapp apps/hello
```

Edit your new application `/apps/hello/app.go`.

Use the same [client](https://github.com/kubernetes/client-go) the rest of Kubernetes uses to express your application.

## Testing your application 

Create a new test for `hello` and edit the tests.

```bash 
cp apps/sampleapp_test.go apps/hello_test.go
```

Then bootstrap a local kind cluster and actually deploy your application to a real Kubernetes cluster.

```bash 
sudo -E make test
```

You can add custom integration tests to check whatever you want.

```go 
func TestHelloAppName(t *testing.T) {
	app := hello.New("default", "hello-app")
	if app.Name != "hello-app" {
		t.Errorf("app Name is not plumbed through from New()")
	}
}
```

## Deploy your application 

You can now deploy your application directly to Kubernetes from the provided CLI tool.

```bash 
make
sudo -E make install
yamyams install hello-app
```

You can also `list` and `uninstall`

```bash 
yamyams list
yamyams uninstall
```
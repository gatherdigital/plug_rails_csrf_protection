# PlugRailsCSRFProtection

Plug to protect from cross-site request forgery in a Rails compatible way.
Copied and adapted from [Plug.CSRFProtection](https://github.com/elixir-lang/plug/blob/master/lib/plug/csrf_protection.ex)

For this plug to work, it expects a session to have been
previously fetched. It will then compare the plug stored
in the session with the one sent by the request to determine
the validity of the request. For an invalid request the action
taken is based on the `:with` option.

The token may be sent by the request either via the params
with key "_csrf_token" or a header with name "x-csrf-token".

GET requests are not protected, as they should not have any
side-effect or change your application state. JavaScript
requests are an exception: by using a script tag, external
websites can embed server-side generated JavaScript, which
can leak information. For this reason, this plug also forbids
any GET JavaScript request that is not XHR (or AJAX).

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `plug_rails_csrf_protection` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [{:plug_rails_csrf, github: "gatherdigital/plug_rails_csrf_protection"}]
end
```

Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/plug_rails_csrf_protection](https://hexdocs.pm/plug_rails_csrf_protection).


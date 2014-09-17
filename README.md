Bundix makes it easy to package your Bundler-enabled applications with the Nix
package manager.

### Is it "Production Ready™"?

![DANGER: EXPERIMENTAL](https://raw.github.com/cryptosphere/cryptosphere/master/images/experimental.png)

Nope. It's work-in-progress.

### Installation

Just clone the repo, Nix can handle everything else.

```
git clone https://github.com/aflatter/bundix
```

### How does it work?

Bundix builds a definition of your Ruby environment using Bundler and writes a
Nix expression for it. The generated expression can then be loaded and all the
Gem handling etc. will now be handled by Nix.

### Usage

1. Change to your project's directory.
2. Generate your definition:
   `nix-shell /path/to/bundix/repo --shell 'bundix expr'`
3. Load the definition using `nixpkgs.loadRubyEnv ./.bundix/definition.nix {}`.


### Known issues

- Git repositories that host multiple gems are not supported yet. A single gem
  per repository will work fine.
- `path` sources are not supported.
- The ruby version specified by your Gemfile is read but not used yet.
  Pass `{ ruby = yourRuby; }` to `loadRubyEnv` instead.

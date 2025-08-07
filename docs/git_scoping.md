# Scoping in Git

When working with Git, you might encounter a situation where most of your repositories should use one set of credentials, but one or two repositories need to recognize you as a different user.

I faced this problem when I started using a client-provided laptop. To get familiar with the machine, I began practicing Git on it. All my personal work was on that machine, and I wanted to push it to my own GitHub account. However, I couldn’t change the global Git configuration because the laptop was set up with the client’s credentials.

That’s when I learned about **Git Scoping**.

## Git Configuration Scopes

Git supports three levels of configuration scope:

- **Local**: Applies to a specific repository (i.e., directory-based).
- **Global**: Applies to the current user across all repositories on the machine.
- **System**: Applies to all users on the entire machine.

## Precedence Order

Git applies configuration settings based on the following order of precedence:

Local > Global > System


This means:

- A setting in the **local** scope overrides the same setting in the **global** or **system** scope.
- A setting in the **global** scope overrides the **system** scope.
- The **system** scope provides the base-level configuration for all users.

## Configuring Git with Scopes

You can use the `git config` command to set configurations at different scopes:

```
# Local scope: only for the current repository
git config --local user.name "Your Name"
git config --local user.email "your.email@example.com"
```

You can use --global or --system instead of --local to change the scope.

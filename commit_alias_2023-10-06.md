Alias for .gitconfig to commit with convetional commits

```
[alias]
	cc = "!f() { \
		read -p \"Type (feat/fix/docs/style/refactor/test/chore): \" type; \
		read -p \"Scope (optional): \" scope; \
		read -p \"Short description: \" desc; \
		read -p \"Breaking change? (y/N): \" breaking; \
		\
		if [ \"${breaking,,}\" = \"y\" ]; then \
			breaking_mark=\"!\"; \
		else \
			breaking_mark=\"\"; \
		fi; \
		\
		if [ -z \"$scope\" ]; then \
			git commit -m \"$type$breaking_mark: $desc\"; \
		else \
			git commit -m \"$type($scope)$breaking_mark: $desc\"; \
		fi; \
	}; f"
```

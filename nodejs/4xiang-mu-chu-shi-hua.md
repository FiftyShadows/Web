##.gitignore

- 匹配模式前/    代表项目根目录

- 匹配模式最后加/    代表是目录

- 匹配模式前加!    代表取反

- *代表任意个字符

- ?匹配任意一个字符

- **匹配多级目录



##.editorconfig

- 安装editorconfig插件

- 配置editorconfig

```
# EditorConfig is awesome: http://EditorConfig.org

# top-most EditorConfig file
root = true

# Apply for all files
[*]

charset = utf-8

indent_style = space
indent_size = 2

end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

[*.json]
indent_size = 4

```


##.eslintrc.js
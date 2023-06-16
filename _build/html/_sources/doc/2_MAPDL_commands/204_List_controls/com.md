# com

```{py:method} Mapdl.com(comment='', **kwargs)

Places a comment in the output.

APDL Command: `/COM`

Parameters:
------------

  comment
  : Comment string, up to 75 characters.\注释字符串，最多 75 个字符。

Notes
-------

The output from this command consists of the comment string. This command is similar to C*** except that the comment produced by C*** is more easily identified in the output. Parameter substitution within the comment occurs for every valid expression delimited by percent (%) signs. Enclosing such an expression in single quotes prevents parameter substitution.\
这条命令的输出由注释字符串组成。这个命令与 C*** 类似，只是 C*** 产生的注释在输出中更容易识别。注释中的参数替换发生在每个以百分号（%）为界的有效表达式上。将这样的表达式用单引号括起来可以防止参数替换。

Another way to include a comment is to precede it with a ! character (on the same line). The ! may be placed anywhere on the line, and any input following it is ignored as a comment. No output is produced by such a comment, but the comment line is included on the log file. This is a convenient way to annotate the log file.\
另一种包含注释的方法是在它前面加上一个 `！` 字符（在同一行）。`!` 可以放在行中的任何地方，它后面的任何输入都会作为注释被忽略。这样的注释不会产生输出，但注释行会被包含在日志文件中。这是一种方便的注释日志文件的方法。

This command is valid anywhere.

```


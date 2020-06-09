# Puppet survival tips

## String interpolation

`$value = "${one}${two}"`

## Use class name in script

`$title` and `$name` are both set to the class name automatically.

## Looping and ranging

This example uses `range` inside a `each` iteration. It will *range* create 9 git repo (proc1 to proc9) inside *each* of the 2 hosts (apps1 and apps3).

```puppet
$a = ['apps1', 'apps3']
$a.each |$host| {
  range("${host}-proc1", "${host}-proc9").each |$repo| {
    gitrep{"${repo}":
      dests               => ["${host}.app.net",],
      postreceivetemplate => "post-receive.erb",
    }
  }
}
```


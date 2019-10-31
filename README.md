## three-full
A quick way to gather all example modules of threejs

## Processing steps

- 1. Using shell to list all modules to a custom file

```shell
cd node_modules/three
egrep "export (const|function|class|interface)" examples/* -nr | grep "\.d\.ts" | awk -F: '{print $1}' | sed s/\.d\.ts//g | sort | uniq | awk '{print "export * from '\''three/" $1 "'\'';"}' > /yourpath/somefile.ts
```

- 2. Deal with conflicts

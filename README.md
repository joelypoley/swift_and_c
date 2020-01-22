# swift_and_c

This repo is a minimal example of calling C from Swift.

## Step-by-step instructions for calling C from Swift

Initialize your Swift package.

```
$ mkdir swift_and_c
$ cd swift_and_c
$ swift package init --type executable
```

Create a new folder `CMath`.

```
$ mkdir Sources/CMath
```

Create a new file `Sources/CMath/Cmath.c` and define a function in there.

```
// Sources/CMath/CMath.c
int square(int x) {
  return x * x;
}
```

Add a new directory `Sources/CMath/include` and create a header file which declares your function.

```
// Sources/CMath/include/CMath.h
int square(int x);
```

Add `CMath` to the Package targets by adding the following snippet to the `targets` array in  `Package.swift`.

```
.target(
  name: "CMath",
  dependencies: []),
```

Modify the `swift_and_c` target to depend on CMath.

```
.target(
  name: "swift_and_c",
  dependencies: ["CMath"]),
```

Modify `Sources/swift_and_c/main.swift` so that it uses the CMath module.

```
// Sources/swift_and_c/main.swift
import CMath

print(square(3))
```

Type 

```
$ swift run
```

and check the output is 9.




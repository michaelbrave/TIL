to start
    swift package init

it will take on the name of the folder it's in and create a few files, the most prominent of which is the *Package.swift* file

modify the *Package.swift* file, it will look something like this:
        // swift-tools-version:5.2
        // The swift-tools-version declares the minimum version of Swift required to build this package.

        import PackageDescription

        let package = Package(
            name: "Revolution_Engine",
            products: [
                // Products define the executables and libraries produced by a package, and make them visible to other packages.
                .library(
                    name: "Revolution_Engine",
                    targets: ["Revolution_Engine"]),
            ],
            dependencies: [
                // Dependencies declare other packages that this package depends on.
                // .package(url: /* package url */, from: "1.0.0"),
            ],
            targets: [
                // Targets are the basic building blocks of a package. A target can define a module or a test suite.
                // Targets can depend on other targets in this package, and on products in packages which this package depends on.
                .target(
                    name: "Revolution_Engine",
                    dependencies: []),
                .testTarget(
                    name: "Revolution_EngineTests",
                    dependencies: ["Revolution_Engine"]),
            ]
        )

things to change are adding dependencies like:
        .package(url: "https://github.com/ctreffs/SwiftSDL2.git", from: "1.0.0")

and then inside the .target - dependencies give it a name like this:
        .target(
            name: "Revolution_Engine",
            dependencies: ["SwiftSDL"]),

when done it should look something like:
        // swift-tools-version:5.2
        // The swift-tools-version declares the minimum version of Swift required to build this package.

        import PackageDescription

        let package = Package(
            name: "Revolution_Engine",
            products: [
                // Products define the executables and libraries produced by a package, and make them visible to other packages.
                .library(
                    name: "Revolution_Engine",
                    targets: ["Revolution_Engine"]),
            ],
            dependencies: [
                // Dependencies declare other packages that this package depends on.
                // .package(url: /* package url */, from: "1.0.0"),
                .package(url: "https://github.com/ctreffs/SwiftSDL2.git", from: "1.0.0")
            ],
            targets: [
                // Targets are the basic building blocks of a package. A target can define a module or a test suite.
                // Targets can depend on other targets in this package, and on products in packages which this package depends on.
                .target(
                    name: "Revolution_Engine",
                    dependencies: ["SwiftSDL"]),
                .testTarget(
                    name: "Revolution_EngineTests",
                    dependencies: ["Revolution_Engine"]),
            ]
        )


after adding and changing dependencies:
    swift package update


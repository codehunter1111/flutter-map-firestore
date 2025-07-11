# Books add-to-app sample

This application simulates a mock scenario in which an existing app with
business logic and middleware already exists. It demonstrates how to add Flutter
to an app that has established patterns for these domains. For more information
on how to use it, see the [README.md](../README.md) parent directory.

This application also utilizes the [Pigeon](https://pub.dev/packages/pigeon)
plugin to avoid manual platform channel wiring. Pigeon autogenerates the
platform channel code in Dart/Java/Objective-C to allow interop using higher
order functions and data classes instead of string-encoded methods and
serialized primitives.

The Pigeon autogenerated code is checked-in and ready to use. If the schema
in `pigeon/schema.dart` is updated, the generated classes can also be re-
generated using:

```shell
flutter pub run pigeon --input pigeon/schema.dart \
  --dart_out lib/api.dart \
  --objc_header_out ../ios_books/IosBooks/api.h \
  --objc_source_out ../ios_books/IosBooks/api.m \
  --objc_prefix BK \
  --java_out ../android_books/app/src/main/java/dev/flutter/example/books/Api.java \
  --java_package "dev.flutter.example.books"
```

## Demonstrated concepts

* An existing books catalog app is already implemented in Kotlin and Swift.
* The platform-side app has existing middleware constraints that should also
  be the middleware foundation for the additional Flutter screen.
    * On Android, the Kotlin app already uses GSON and OkHttp for networking and
      references the Google Books API as a data source. These same libraries
      also underpin the data fetched and shown in the Flutter screen.
* The platform application interfaces with the Flutter book details page using
  idiomatic platform API conventions rather than Flutter conventions.
    * On Android, the Flutter activity receives the book to show via activity
      intent and returns the edited book by setting the result intent on the
      activity. No Flutter concepts are leaked into the consumer activity.
* The [pigeon](https://pub.dev/packages/pigeon) plugin is used to generate
  interop APIs and data classes. The same `Book` model class is used within the
  Kotlin/Swift program, the Dart program and in the interop between Kotlin/Swift
  and Dart.

## More info
<!-- 
 - This is for zero and two private. Reference metadata.
 - Target directory credentials and encrypted text file.
 - GP for password example and real password as target directory text file(4#E+#4, Syllable Cap).
 - Hashed Buy Coffee Now.
 - Helper resource to target output text file.
 - One Two minus rule for encrypts. Swap the two public keys.
   Hexademical rules
 -->


For more information about Flutter, check out
[flutter.dev](https://flutter.dev).

For instructions on how to integrate Flutter modules into your existing
applications, see Flutter's
[add-to-app documentation](https://flutter.dev/docs/development/add-to-app).

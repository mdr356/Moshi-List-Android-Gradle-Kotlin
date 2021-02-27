# Moshi | List | Android | Gradle | Kotlin
A modern, powerful JSON library use for serialization and deserialization with little effort.

## Gradle
```kotlin
implementation("com.squareup.moshi:moshi:<version")
```android

## sample.json
```json
[ 
  {
    "imageFile": "account1Image",
    "accountName": "Spook",
    "description": "Spook is mean",
    "account value": 20000

  },
  {
    "imageFile": "account2Image",
    "accountName": "Spook",
    "description": "Spook is mean",
    "account value": 1000

  }
]
```

## Kotlin Data class
```kotlin
data class Account (
  val imageFile: String? = null,
  val accountName: String? = null,
  val description: String? = null,
  @Json(name = "account value")
  val accountValue: Int? = null
)
```

Use @Json to map fiels to JSON names.

## Moshi Builder
```kotlin
val moshi : Moshi = Moshi.Builder()
    .add(KotlinJsonAdapterFactory())
    .build()
```

## Moshi Adapter 
```kotlin
private val listType = Types.newParameterizedType(
        List::class.java, Account::class.java
    )

val adapter: JsonAdapter<List<Account>> = moshi.adapter(listType)
```

## Data type from json
```kotlin
val account : List<Account> = adapter.fromJson(sample.json)
```

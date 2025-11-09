* `NSManagedObject` is the Model which we create for Entity
* `NSManagedObjectContext` is the one responsible for tracking everything happens to `NSManagedObject` like all the CRUD operations it keeps track them all
* `NSPersistentContainer` is the one which holds sqlite Database
* `PersistentContainer` is the custom class which we create in which we connect our DataModel which we create in xcode, in whcih we have entites and attributes
* `NSPersistentStore` actual sqllit database storage

```swift
MyModel.xcdatamodeld// this is the one which we create in our xcode for our datamodel
```
```swift
 ┌────────────────────────────────────────────────────────────┐
 │                    PersistenceController                   │
 │   (Your custom struct/class that sets up Core Data Stack)  │
 │                                                            │
 │   ┌────────────────────────────────────────────────────┐   │
 │   │               NSPersistentContainer                │   │
 │   │  (Manages Core Data stack & connects to SQLite)    │   │
 │   │                                                    │   │
 │   │   ┌────────────────────────────────────────────┐   │   │
 │   │   │          NSPersistentStore (SQLite)         │   │   │
 │   │   │   (Actual on-disk database storage)         │   │   │
 │   │   └────────────────────────────────────────────┘   │   │
 │   │                                                    │   │
 │   │   ┌────────────────────────────────────────────┐   │   │
 │   │   │        NSManagedObjectContext              │   │   │
 │   │   │ (Tracks all CRUD changes in memory)        │   │   │
 │   │   │                                            │   │   │
 │   │   │    ┌──────────────────────────────────┐    │   │   │
 │   │   │    │        NSManagedObject           │    │   │   │
 │   │   │    │ (Model for an Entity, e.g.       │    │   │   │
 │   │   │    │  TransactionItem)                │    │   │   │
 │   │   │    └──────────────────────────────────┘    │   │   │
 │   │   └────────────────────────────────────────────┘   │   │
 │   └────────────────────────────────────────────────────┘   │
 └────────────────────────────────────────────────────────────┘

         ▲
         │ connects to
         ▼
     MyModel.xcdatamodeld
   (Your Data Model file in Xcode,
    defines Entities & Attributes)
```

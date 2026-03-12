classDiagram
    class Customer {
        -String id
        -String name
        -String email
        -String phone
        -Order[] purchaseHistory
        -DateTime createdAt
        +isVerified() Boolean
        +addOrder(order Order) void
        +getOrderHistory() Order[]
        +updateProfile(name String, email String) void
    }

    class Order {
        -String id
        -String customerId
        -MenuItem[] items
        -String status
        -DateTime createdAt
        +addItem(item MenuItem) void
        +removeItem(itemId String) void
        +computeTotal() Float
        +getItemCount() Integer
    }

    class MenuItem {
        -String id
        -String name
        -Float price
        -String category
        -Float popularityRating
        -String description
        -Boolean isAvailable
        +updatePrice(price Float) void
        +toggleAvailability() void
        +incrementPopularity() void
    }

    class Menu {
        -String id
        -String name
        -MenuItem[] items
        -DateTime updatedAt
        +addItem(item MenuItem) void
        +removeItem(itemId String) void
        +filterByCategory(category String) MenuItem[]
        +getAllItems() MenuItem[]
        +searchByName(name String) MenuItem[]
    }

    Customer "1" --> "1..*" Order : places
    Order "1" --> "1..*" MenuItem : contains
    Menu "1" --> "0..*" MenuItem : holds

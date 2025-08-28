# ABC Retailer Web App - Part 1

An **ASP.NET Core MVC application** that demonstrates how to use **Azure Storage services**:
- **Blob Storage** – Store and retrieve images/files.
- **Queue Storage** – Send and receive messages (e.g., audit logs).
- **File Share Storage** – Upload, download, and manage files in Azure File Shares.
- **Table Storage** – Store structured NoSQL-style data such as customer profiles.

---

## 🚀 Getting Started

### 1. Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- An [Azure Storage Account](https://portal.azure.com)
- Connection string from your Storage Account

### 2. Configuration
Update `appsettings.json` with your storage account connection string:

```json
{
  "ConnectionStrings": {
    "AzureStorage": "DefaultEndpointsProtocol=https;AccountName=...;AccountKey=...;EndpointSuffix=core.windows.net"
  }
}
````

### 3. Run the App

```bash
dotnet build
dotnet run
```

Navigate to `https://localhost:5001` (or as shown in console).

---

## 📦 Features

### Blob Storage

* Upload files (e.g., images, documents)
* List all uploaded blobs
* Download or delete files
  
*Buisness Logic could be applied to store the blob item URL in a table, like if each Product had one picture or video*

### File Share Storage

* Upload/download files to Azure File Shares
* Manage shared files via UI

*Each item can only be downloaded as the File Share is only supposed to act as a kind of cloud based external drive to store documents.*

### Queue Storage

* Send structured messages (e.g., audit logs)
* Peek and dequeue messages
* Useful for async event processing

*Buisness Logic implemented later could have orders to be serialised to JSON to add to the queue then some logic could happen like an order being marked for delivery where the order queue can deserialise the data into a model update say the status and requeue. Other buisness logic could also be implemeted that when an order is placed and stock runs below a threshold a message can be added to the inventory queue to wait on employee or automation to arrage for more stock for that item to be ordered and so on.*


### Table Storage

* Store customer profiles and structured entities
* CRUD operations via UI
* Uses `ITableEntity` for schema-flexible storage
  
*Later Some table rows could contain association to multimedia that is stored in the blob*



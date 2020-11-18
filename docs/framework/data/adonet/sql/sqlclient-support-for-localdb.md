---
title: Prise en charge de SqlClient pour LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824478"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="3315c-102">Prise en charge de SqlClient pour LocalDB</span><span class="sxs-lookup"><span data-stu-id="3315c-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="3315c-103">Cet article explique comment se connecter à une base de données de base de données locale.</span><span class="sxs-lookup"><span data-stu-id="3315c-103">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="3315c-104">La base de données locale est une version allégée de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3315c-104">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="3315c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="3315c-105">Remarks</span></span>
  
 <span data-ttu-id="3315c-106">Pour résumer ce que vous pouvez faire avec LocalDB :</span><span class="sxs-lookup"><span data-stu-id="3315c-106">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="3315c-107">Créez et démarrez des instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="3315c-107">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="3315c-108">Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB.</span><span class="sxs-lookup"><span data-stu-id="3315c-108">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="3315c-109">Par exemple : `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="3315c-109">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="3315c-110">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance LocalDB.</span><span class="sxs-lookup"><span data-stu-id="3315c-110">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="3315c-111">Quand vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database`, la base de données est supprimée de l’instance LocalDB quand l’application se ferme.</span><span class="sxs-lookup"><span data-stu-id="3315c-111">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="3315c-112">Spécifiez une instance LocalDB dans votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="3315c-112">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="3315c-113">Par exemple, si le nom de votre instance est `myInstance`, la chaîne de connexion inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3315c-113">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="3315c-114">`User Instance=True` n’est pas autorisé lors de la connexion à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="3315c-114">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="3315c-115">Pour plus d’informations sur l’installation de la base de données locale, consultez [SQL Server Express](/sql/database-engine/configure-windows/sql-server-express-localdb)de base.</span><span class="sxs-lookup"><span data-stu-id="3315c-115">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="3315c-116">Créer par programme une instance nommée</span><span class="sxs-lookup"><span data-stu-id="3315c-116">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="3315c-117">Une application peut créer une instance nommée et spécifier une base de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="3315c-117">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="3315c-118">Spécifiez les instances LocalDB à créer dans le fichier app.config, comme suit.</span><span class="sxs-lookup"><span data-stu-id="3315c-118">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="3315c-119">Le numéro de version de l’instance doit être le même que le numéro de version de votre installation de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="3315c-119">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="3315c-120">Spécifiez le nom de l’instance à l’aide du mot clé de chaîne de connexion `server`.</span><span class="sxs-lookup"><span data-stu-id="3315c-120">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="3315c-121">Le nom de l’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="3315c-121">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="3315c-122">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.</span><span class="sxs-lookup"><span data-stu-id="3315c-122">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3315c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3315c-123">See also</span></span>

- [<span data-ttu-id="3315c-124">Fonctionnalités de SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3315c-124">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="3315c-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3315c-125">ADO.NET Overview</span></span>](../ado-net-overview.md)

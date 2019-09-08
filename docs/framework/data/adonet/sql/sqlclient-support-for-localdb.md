---
title: Prise en charge de SqlClient pour LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 200db3b1014278e711062bcbdff81be8d27c3351
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780769"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="6d0f0-102">Prise en charge de SqlClient pour LocalDB</span><span class="sxs-lookup"><span data-stu-id="6d0f0-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="6d0f0-103">À compter de SQL Server nom de code Denali, une version allégée de SQL Server, appelée base de données locale, sera disponible.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="6d0f0-104">Cette rubrique explique comment se connecter à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d0f0-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6d0f0-105">Remarks</span></span>  
 <span data-ttu-id="6d0f0-106">Pour plus d’informations sur la base de données locale, notamment sur l’installation de la base de données locale et configurer votre instance de base de données locale, consultez Documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d0f0-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6d0f0-107">Pour résumer les opérations possibles avec LocalDB :</span><span class="sxs-lookup"><span data-stu-id="6d0f0-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="6d0f0-108">Créez et démarrez les instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="6d0f0-109">Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="6d0f0-110">Par exemple, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="6d0f0-111">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="6d0f0-112">Lorsque vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database` , la base de données sera supprimée de l'instance de LocalDB lorsque l'application se ferme.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="6d0f0-113">Spécifiez une instance de LocalDB dans votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="6d0f0-114">Par exemple, si le nom de l'instance est `myInstance`, la chaîne de connexion est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6d0f0-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="6d0f0-115">Vous ne pouvez pas utiliser`User Instance=True` lors de la connexion à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="6d0f0-116">Vous pouvez télécharger LocalDB à partir de [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="6d0f0-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="6d0f0-117">Si vous souhaitez utiliser SQLCMD. exe pour modifier des données dans votre instance de base de données locale, vous aurez besoin de sqlcmd de SQL Server 2012, que vous pouvez également récupérer à partir de la SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="6d0f0-118">Créer par programme une instance nommée</span><span class="sxs-lookup"><span data-stu-id="6d0f0-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="6d0f0-119">Une application peut créer une instance nommée et spécifier une base de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="6d0f0-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="6d0f0-120">Spécifiez les instances de LocalDB à créer dans le fichier app.config, comme suit.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="6d0f0-121">Le numéro de version de l'instance doit être le même que le numéro de version de votre installation de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="6d0f0-122">Spécifiez le nom de l'instance à l'aide du mot clé de chaîne de connexion `server` .</span><span class="sxs-lookup"><span data-stu-id="6d0f0-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="6d0f0-123">Le nom d’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="6d0f0-124">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0f0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d0f0-125">See also</span></span>

- [<span data-ttu-id="6d0f0-126">Fonctionnalités SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6d0f0-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="6d0f0-127">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6d0f0-127">ADO.NET Overview</span></span>](../ado-net-overview.md)

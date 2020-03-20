---
title: 'Comment : définir la chaîne de connexion'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150569"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="ded19-102">Comment : définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="ded19-102">How to: Define the Connection String</span></span>

<span data-ttu-id="ded19-103">Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="ded19-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="ded19-104">Ce sujet est basé sur le modèle conceptuel [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="ded19-105">Le modèle de vente AdventureWorks est utilisé dans tous les sujets liés aux tâches dans la documentation du Cadre d’entité.</span><span class="sxs-lookup"><span data-stu-id="ded19-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="ded19-106">Ce sujet suppose que vous avez déjà configuré le cadre d’entité et défini le modèle de vente AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ded19-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ded19-107">Pour plus d’informations, voir [Comment : Définir manuellement le modèle et cartographier les fichiers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ded19-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="ded19-108">Les procédures dans ce sujet sont également incluses dans [Comment configurer manuellement un projet-cadre d’entité.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="ded19-109">Si vous utilisez l’Entité Data Model Wizard dans un projet Visual Studio, il génère automatiquement un fichier .edmx et configure le projet pour utiliser le cadre d’entité.</span><span class="sxs-lookup"><span data-stu-id="ded19-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="ded19-110">Pour plus d’informations, voir [Comment : Utilisez l’Assistant modèle de données d’entité.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="ded19-111">Pour définir la chaîne de connexion Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ded19-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="ded19-112">Ouvrez le fichier de configuration de l'application (app.config) du projet et ajoutez la chaîne de connexion suivante :</span><span class="sxs-lookup"><span data-stu-id="ded19-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="ded19-113">Si votre projet ne dispose pas d’un fichier de configuration d’application, vous pouvez en ajouter un en sélectionnant **un nouvel élément** dans le menu du **projet,** en sélectionnant la catégorie **Générale,** en sélectionnant le **fichier de configuration d’application,** puis en cliquant sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="ded19-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ded19-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ded19-114">See also</span></span>

- <span data-ttu-id="ded19-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="ded19-116">[Procédure : créer un fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="ded19-117">[Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ded19-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

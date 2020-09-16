---
title: 'Procédure : Définir la chaîne de connexion'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9b029644e0d4e4c7467fbe1e1144579e6edb3478
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536208"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="38dcf-102">Procédure : Définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="38dcf-102">How to: Define the Connection String</span></span>

<span data-ttu-id="38dcf-103">Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="38dcf-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="38dcf-104">Cette rubrique est basée sur le modèle conceptuel de [ventes AdventureWorks](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="38dcf-104">This topic is based on the [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="38dcf-105">Le modèle de vente AdventureWorks Sales Model est utilisé dans les rubriques relatives aux tâches de la documentation de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="38dcf-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="38dcf-106">Cette rubrique suppose que vous avez déjà configuré le Entity Framework et défini le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="38dcf-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="38dcf-107">Pour plus d’informations, consultez [Comment : définir manuellement les fichiers de modèle et de mappage](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38dcf-107">For more information, see [How to: Manually Define the Model and Mapping Files](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="38dcf-108">Les procédures de cette rubrique sont également incluses dans [procédure : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38dcf-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="38dcf-109">Si vous utilisez l’Assistant Entity Data Model dans un projet Visual Studio, il génère automatiquement un fichier. edmx et configure le projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="38dcf-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="38dcf-110">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38dcf-110">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="38dcf-111">Pour définir la chaîne de connexion Entity Framework</span><span class="sxs-lookup"><span data-stu-id="38dcf-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="38dcf-112">Ouvrez le fichier de configuration de l'application (app.config) du projet et ajoutez la chaîne de connexion suivante :</span><span class="sxs-lookup"><span data-stu-id="38dcf-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="38dcf-113">Si votre projet n’a pas de fichier de configuration de l’application, vous pouvez en ajouter un en sélectionnant **Ajouter un nouvel élément** dans le menu **projet** , en sélectionnant la catégorie **général** , en sélectionnant fichier de configuration de l' **application**, puis en cliquant sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="38dcf-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="38dcf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38dcf-114">See also</span></span>

- <span data-ttu-id="38dcf-115">[Démarrage rapide](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38dcf-115">[Quickstart](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="38dcf-116">[Procédure : créer un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38dcf-116">[How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="38dcf-117">[Outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38dcf-117">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

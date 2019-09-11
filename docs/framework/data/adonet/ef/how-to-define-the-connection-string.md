---
title: 'Procédure : Définir la chaîne de connexion'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854660"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="49881-102">Procédure : Définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="49881-102">How to: Define the Connection String</span></span>

<span data-ttu-id="49881-103">Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="49881-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="49881-104">Cette rubrique est basée sur le modèle conceptuel de [ventes AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="49881-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="49881-105">Le modèle de vente AdventureWorks Sales Model est utilisé dans les rubriques relatives aux tâches de la documentation de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="49881-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="49881-106">Cette rubrique suppose que vous avez déjà configuré le Entity Framework et défini le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="49881-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="49881-107">Pour plus d’informations, consultez [Guide pratique pour Définissez manuellement les fichiers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))de modèle et de mappage.</span><span class="sxs-lookup"><span data-stu-id="49881-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="49881-108">Les procédures de cette rubrique sont également incluses dans [procédure : Configurez manuellement un](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))projet Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="49881-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="49881-109">Si vous utilisez l’Assistant Entity Data Model dans un projet Visual Studio, il génère automatiquement un fichier. edmx et configure le projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="49881-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="49881-110">Pour plus d’informations, consultez [Guide pratique pour Utiliser l’Assistant Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49881-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="49881-111">Pour définir la chaîne de connexion Entity Framework</span><span class="sxs-lookup"><span data-stu-id="49881-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="49881-112">Ouvrez le fichier de configuration de l'application (app.config) du projet et ajoutez la chaîne de connexion suivante :</span><span class="sxs-lookup"><span data-stu-id="49881-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="49881-113">Si votre projet n’a pas de fichier de configuration de l’application, vous pouvez en ajouter un en sélectionnant **Ajouter un nouvel élément** dans le menu **projet** , en sélectionnant la catégorie **général** , en sélectionnant fichier de configuration de l' **application**, puis en cliquant sur **Ajoutez**.</span><span class="sxs-lookup"><span data-stu-id="49881-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="49881-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49881-114">See also</span></span>

- <span data-ttu-id="49881-115">[Démarrage rapide](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49881-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="49881-116">[Guide pratique pour Créer un nouveau fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49881-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="49881-117">[Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49881-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

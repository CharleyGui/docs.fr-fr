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
# <a name="how-to-define-the-connection-string"></a>Procédure : Définir la chaîne de connexion

Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel. Cette rubrique est basée sur le modèle conceptuel de [ventes AdventureWorks](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . Le modèle de vente AdventureWorks Sales Model est utilisé dans les rubriques relatives aux tâches de la documentation de Entity Framework. Cette rubrique suppose que vous avez déjà configuré le Entity Framework et défini le modèle de vente AdventureWorks Sales Model. Pour plus d’informations, consultez [Comment : définir manuellement les fichiers de modèle et de mappage](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Les procédures de cette rubrique sont également incluses dans [procédure : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Si vous utilisez l’Assistant Entity Data Model dans un projet Visual Studio, il génère automatiquement un fichier. edmx et configure le projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Pour définir la chaîne de connexion Entity Framework

- Ouvrez le fichier de configuration de l'application (app.config) du projet et ajoutez la chaîne de connexion suivante :

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Si votre projet n’a pas de fichier de configuration de l’application, vous pouvez en ajouter un en sélectionnant **Ajouter un nouvel élément** dans le menu **projet** , en sélectionnant la catégorie **général** , en sélectionnant fichier de configuration de l' **application**, puis en cliquant sur **Ajouter**.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Procédure : créer un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

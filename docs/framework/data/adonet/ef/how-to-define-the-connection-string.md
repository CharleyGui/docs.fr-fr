---
title: 'Procédure : Définir la chaîne de connexion'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833954"
---
# <a name="how-to-define-the-connection-string"></a>Procédure : Définir la chaîne de connexion

Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel. Cette rubrique est basée sur le modèle conceptuel de [ventes AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . Le modèle de vente AdventureWorks Sales Model est utilisé dans les rubriques relatives aux tâches de la documentation de Entity Framework. Cette rubrique suppose que vous avez déjà configuré le Entity Framework et défini le modèle de vente AdventureWorks Sales Model. Pour plus d'informations, voir [Procédure : Définissez manuellement les fichiers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))de modèle et de mappage. Les procédures de cette rubrique sont également incluses dans [procédure : Configurez manuellement un](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))projet Entity Framework.

> [!NOTE]
> Si vous utilisez l’Assistant Entity Data Model dans un projet Visual Studio, il génère automatiquement un fichier. edmx et configure le projet pour qu’il utilise le Entity Framework. Pour plus d'informations, voir [Procédure : Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.

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

Si votre projet n’a pas de fichier de configuration de l’application, vous pouvez en ajouter un en sélectionnant **Ajouter un nouvel élément** dans le menu **projet** , en sélectionnant la catégorie **général** , en sélectionnant fichier de configuration de l' **application**, puis en cliquant sur **Ajoutez**.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Guide pratique pour Créer un nouveau fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

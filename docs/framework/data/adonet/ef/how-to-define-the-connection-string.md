---
title: 'Procédure : Définir la chaîne de connexion'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 8386f93d0e80aa824b1e91a130812b9b3a2b3619
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306383"
---
# <a name="how-to-define-the-connection-string"></a>Procédure : Définir la chaîne de connexion

Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel. Cette rubrique est basée sur le [AdventureWorks Sales Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) modèle conceptuel. Le modèle de vente AdventureWorks Sales Model est utilisé dans toutes les rubriques liées aux tâches de la documentation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Cette rubrique suppose que vous avez déjà configuré le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et défini le modèle AdventureWorks Sales Model. Pour plus d'informations, voir [Procédure : Définir le modèle manuellement et de fichiers de mappage](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Les procédures décrites dans cette rubrique sont également incluses dans [Comment : Configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Si vous utilisez l’Assistant Entity Data Model dans un projet Visual Studio, il génère un fichier .edmx et configure automatiquement le projet à utiliser le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Pour plus d'informations, voir [Procédure : Utilisez l’Assistant Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

Si votre projet n’a pas d’un fichier de configuration d’application, vous pouvez en ajouter un en sélectionnant **ajouter un nouvel élément** à partir de la **projet** menu, en sélectionnant le **général** catégorie, en sélectionnant **fichier de Configuration d’Application**, puis en cliquant sur **ajouter**.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Guide pratique pour Créez un fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

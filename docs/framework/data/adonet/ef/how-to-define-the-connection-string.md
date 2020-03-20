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
# <a name="how-to-define-the-connection-string"></a>Comment : définir la chaîne de connexion

Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel. Ce sujet est basé sur le modèle conceptuel [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) Le modèle de vente AdventureWorks est utilisé dans tous les sujets liés aux tâches dans la documentation du Cadre d’entité. Ce sujet suppose que vous avez déjà configuré le cadre d’entité et défini le modèle de vente AdventureWorks. Pour plus d’informations, voir [Comment : Définir manuellement le modèle et cartographier les fichiers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Les procédures dans ce sujet sont également incluses dans [Comment configurer manuellement un projet-cadre d’entité.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))

> [!NOTE]
> Si vous utilisez l’Entité Data Model Wizard dans un projet Visual Studio, il génère automatiquement un fichier .edmx et configure le projet pour utiliser le cadre d’entité. Pour plus d’informations, voir [Comment : Utilisez l’Assistant modèle de données d’entité.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

Si votre projet ne dispose pas d’un fichier de configuration d’application, vous pouvez en ajouter un en sélectionnant **un nouvel élément** dans le menu du **projet,** en sélectionnant la catégorie **Générale,** en sélectionnant le **fichier de configuration d’application,** puis en cliquant sur **Add**.

## <a name="see-also"></a>Voir aussi

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Procédure : créer un fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

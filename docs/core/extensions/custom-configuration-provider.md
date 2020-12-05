---
title: Implémenter un fournisseur de configuration personnalisé dans .NET
description: Découvrez comment implémenter un fournisseur de configuration personnalisé dans des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740116"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a>Implémenter un fournisseur de configuration personnalisé dans .NET

De nombreux [fournisseurs de configuration](configuration-providers.md) sont disponibles pour les sources de configuration courantes, telles que les fichiers JSON, XML et ini. Vous devrez peut-être implémenter un fournisseur de configuration personnalisé lorsque l’un des fournisseurs disponibles ne répond pas aux besoins de votre application. Dans cet article, vous allez apprendre à implémenter un fournisseur de configuration personnalisé qui s’appuie sur une base de données comme source de configuration.

## <a name="custom-configuration-provider"></a>Fournisseur de configuration personnalisé

L’exemple d’application montre comment créer un fournisseur de configuration de base qui lit les paires clé-valeur de configuration à partir d’une base de données à l’aide d' [Entity Framework (EF) Core](/ef/core).

Le fournisseur présente les caractéristiques suivantes :

- La base de données en mémoire EF est utilisée à des fins de démonstration. Pour utiliser une base de données qui nécessite une chaîne de connexion, implémentez un autre `ConfigurationBuilder` pour fournir la chaîne de connexion à partir d’un autre fournisseur de configuration.
- Le fournisseur lit une table de base de données dans la configuration au démarrage. Le fournisseur n’interroge pas la base de données par clé.
- Le rechargement en cas de changement n’est pas implémenté, par conséquent, la mise à jour la base de données après le démarrage de l’application n’a aucun effet sur la configuration de l’application.

Définissez une `Settings` entité de type d’enregistrement pour le stockage des valeurs de configuration dans la base de données. Par exemple, vous pouvez ajouter un fichier *Settings.cs* dans votre dossier de *modèles* :

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

Pour plus d’informations sur les types d’enregistrements, consultez [types d’enregistrements en C# 9](../../csharp/whats-new/csharp-9.md#record-types).

Ajoutez un `EntityConfigurationContext` pour stocker les valeurs configurées et y accéder.

*Fournisseurs/EntityConfigurationContext. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

Créez une classe qui implémente <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.

*Fournisseurs/EntityConfigurationSource. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

Créez le fournisseur de configuration personnalisé en héritant de <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>. Le fournisseur de configuration initialise la base de données quand elle est vide. Étant donné que les clés de configuration ne respectent pas la casse, le dictionnaire utilisé pour initialiser la base de données est créé avec le comparateur ne respectant pas la casse ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).

*Fournisseurs/EntityConfigurationProvider. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

Une `AddEntityConfiguration` méthode d’extension autorise l’ajout de la source de configuration à une <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.

*Extensions/ConfigurationBuilderExtensions. cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

Le code suivant montre comment utiliser le `EntityConfigurationProvider` personnalisé dans *Program.cs* :

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a>Voir aussi

- [Configuration dans .NET](configuration.md)
- [Fournisseurs de configuration dans .NET](configuration-providers.md)

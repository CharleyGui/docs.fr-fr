---
title: Changements cassants et bibliothèques .NET
description: Recommandations relatives aux bonnes pratiques pour parcourir les changements cassants lors de la création de bibliothèques .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223329"
---
# <a name="breaking-changes"></a>Changements cassants

Il est important pour une bibliothèque .NET de trouver un équilibre entre la stabilité pour les utilisateurs existants et l’innovation pour l’avenir. Les auteurs de bibliothèques tendent à refactoriser et repenser le code jusqu’à ce qu’il soit parfait, mais les changements cassants peuvent avoir un impact négatif sur vos utilisateurs existants, surtout pour les bibliothèques de bas niveau.

## <a name="project-types-and-breaking-changes"></a>Types de projets et changements cassants

La façon dont une bibliothèque est utilisée par la communauté .NET modifie l’effet des changements cassants sur les développeurs utilisateurs finaux.

- Les **bibliothèques de bas niveau et de niveau intermédiaire** comme les sérialiseurs, les analyseurs HTML, les outils de mappage objet-relationnel de base de données ou les frameworks web, sont les plus affectées par les changements cassants.

  Les packages de modules sont utilisés par les développeurs utilisateurs finaux pour générer des applications et par d’autres bibliothèques comme dépendances NuGet. Par exemple, vous créez une application et utilisez un client open source pour appeler un service web. Une mise à jour cassante apportée à une dépendance qu’utilise le client n’est pas quelque chose que vous pouvez résoudre. C’est le client open source qui doit être changé, mais vous n’avez aucun contrôle là-dessus. Vous devez rechercher des versions compatibles des bibliothèques ou envoyer un correctif à la bibliothèque cliente et attendre une nouvelle version. Le pire des cas se présente si vous voulez utiliser deux bibliothèques qui dépendent de versions mutuellement incompatibles d’une troisième bibliothèque.

- Les **bibliothèques de haut niveau** comme les suites de contrôles d’interface utilisateur sont moins sensibles aux changements cassants.

  Les bibliothèques de haut niveau sont directement référencées dans une application pour l’utilisateur final. En cas de changements cassants, le développeur peut choisir de procéder à la mise à jour vers la dernière version ou modifier son application pour les utiliser.

✔️ À FAIRE : Réfléchir à la façon dont votre bibliothèque sera utilisée. Quel sera l’effet des changements cassants sur les applications et les bibliothèques qui l’utilisent ?

✔️ À FAIRE : Réduire les changements cassants lors du développement d’une bibliothèque .NET de bas niveau.

✔️ À ENVISAGER : Publier un remaniement majeur d’une bibliothèque en tant que nouveau package NuGet.

## <a name="types-of-breaking-changes"></a>Types de changements cassants

Les changements cassants sont répartis en différentes catégories et n’ont pas tous le même impact.

### <a name="source-breaking-change"></a>Changement cassant source

Un changement cassant source n’affecte pas l’exécution du programme, mais provoque des erreurs de compilation la prochaine fois que l’application est recompilée. Par exemple, une nouvelle surcharge peut créer une ambiguïté dans les appels de méthode qui étaient précédemment non équivoques, ou un paramètre renommé peut casser des appelants qui utilisent des paramètres nommés.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Comme un changement cassant source est uniquement nuisible quand les développeurs recompilent leurs applications, il s’agit de celui qui entraîne le moins de perturbations. Les développeurs peuvent facilement résoudre leur propre code source rompu.

### <a name="behavior-breaking-change"></a>Changement cassant de comportement

Les changements de comportement sont le type le plus courant de changement cassant : presque n’importe quel changement de comportement peut impacter une personne. Les changements apportés à votre bibliothèque, comme les signatures de méthode, les exceptions levées ou les formats de données d’entrée ou de sortie, peuvent tous avoir un impact négatif sur les consommateurs de celle-ci. Même un correctif de bogue peut être considéré comme un changement cassant si les utilisateurs s’appuyaient sur le comportement précédemment rompu.

L’ajout de fonctionnalités et l’amélioration des comportements médiocres sont une bonne chose, mais la mise à niveau peut s’avérer très difficile pour les utilisateurs existants sans les précautions nécessaires. Une approche pour aider les développeurs à gérer les changements cassants de comportement consiste à les masquer derrière des paramètres. Les paramètres permettent aux développeurs d’effectuer la mise à jour vers la dernière version de votre bibliothèque tout en choisissant d’adhérer ou non aux changements cassants. Cette stratégie permet aux développeurs de rester à jour tout en permettant à leur code de consommation de s’adapter au fil du temps.

Par exemple, ASP.NET Core MVC présente le concept d’une [version de compatibilité](/aspnet/core/mvc/compatibility-version) qui modifie les fonctionnalités activées et désactivées sur `MvcOptions`.

✔️ À ENVISAGER : Omettre de nouvelles fonctionnalités par défaut si elles affectent les utilisateurs existants et permettre aux développeurs d’adhérer à la fonctionnalité avec un paramètre.

### <a name="binary-breaking-change"></a>Changement cassant binaire

Un changement cassant binaire se produit quand vous modifiez l’API publique de votre bibliothèque ; les assemblys compilés avec des versions antérieures de votre bibliothèque ne sont plus en mesure d’appeler l’API. Par exemple, la modification de la signature d’une méthode en ajoutant un nouveau paramètre amène les assemblys compilés avec la version antérieure de la bibliothèque à lever une <xref:System.MissingMethodException>.

Un changement cassant binaire peut également casser un **assembly entier**. Le renommage d’un assembly avec `AssemblyName` change l’identité de l’assembly, de même que l’ajout, la suppression ou le changement de la clé d’affectation de noms forts de l’assembly. Un changement de l’identité d’un assembly va casser tout le code compilé qui l’utilise.

❌ NE modifiez pas le nom d’un assembly.

❌ N’ajoutez pas, ne supprimez pas ou ne modifiez pas la clé de nom fort.

✔️ À ENVISAGER : Utiliser des classes de base abstraites plutôt que des interfaces.

> L’ajout de n’importe quel élément à une interface entraîne l’échec des types existants qui l’implémentent. Une classe de base abstraite vous permet d’ajouter une implémentation virtuelle par défaut.

✔️ À ENVISAGER : Placer le <xref:System.ObsoleteAttribute> sur les types et membres que vous envisagez de supprimer. L’attribut doit comporter des instructions pour la mise à jour du code afin de ne plus utiliser l’API obsolète.

> Le code qui appelle des types et méthodes avec le <xref:System.ObsoleteAttribute> génère un avertissement de génération avec le message fourni à l’attribut. Les avertissements donnent aux personnes qui utilisent la surface d’API obsolète le temps de migrer afin que la plupart ne l’utilisent plus quand elle est supprimée.

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

✔️ À ENVISAGER : Conserver les types et méthodes avec le <xref:System.ObsoleteAttribute> indéfiniment dans les bibliothèques de bas niveau et de niveau intermédiaire.

> La suppression des API est un changement cassant binaire. Envisagez de conserver les méthodes et types obsolètes si leur mise à jour présente un faible coût et n’ajoute pas beaucoup de dette technique à votre bibliothèque. Le fait de ne pas supprimer les types et méthodes peut permettre d’éviter les pires scénarios mentionnés ci-dessus.

## <a name="see-also"></a>Voir aussi

- [Considérations relatives à la version et la mise à jour pour les développeurs C#](../../csharp/whats-new/version-update-considerations.md)
- [A definitive guide to API-breaking changes in .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [Règles de modification avec rupture .NET](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Précédent](versioning.md)

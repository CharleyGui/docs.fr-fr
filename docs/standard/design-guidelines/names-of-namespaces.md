---
title: Noms d'espaces de noms
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744139"
---
# <a name="names-of-namespaces"></a>Noms d'espaces de noms
Comme pour les autres instructions d’affectation de noms, l’objectif de l’attribution de noms aux espaces de noms est de créer suffisamment de clarté pour le programmeur qui utilise l’infrastructure pour savoir immédiatement ce que le contenu de l’espace de noms est susceptible d’être. Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 Voici quelques exemples :

 `Fabrikam.Math` `Litware.Security`

 ✔️ FAITES précéder les noms d’espaces de noms d’un nom de société pour empêcher les espaces de noms de sociétés différentes d’avoir le même nom.

 ✔️ Utilisez un nom de produit stable et indépendant de la version au deuxième niveau d’un nom d’espace de noms.

 ❌ n’utilisez pas de hiérarchies organisationnelles comme base pour les noms dans les hiérarchies d’espaces de noms, car les noms de groupe dans les sociétés ont tendance à être éphémères. Organiser la hiérarchie des espaces de noms autour des groupes de technologies associées.

 ✔️ Utilisez PascalCasing et séparez les composants d’espace de noms par des points (par exemple, `Microsoft.Office.PowerPoint`). Si votre personnalisation utilise une casse qui n’est pas traditionnelle, vous devez suivre la casse définie par votre personnalisation, même si elle diffère de la casse normale des espaces de noms.

 ✔️ envisagez d’utiliser des noms d’espaces de noms pluriels lorsque cela est approprié.

 Par exemple, utilisez `System.Collections` à la place de `System.Collection`. Toutefois, les noms et les acronymes sont des exceptions à cette règle. Par exemple, utilisez `System.IO` à la place de `System.IOs`.

 ❌ n’utilisez pas le même nom pour un espace de noms et un type dans cet espace de noms.

 Par exemple, n’utilisez pas `Debug` comme nom d’espace de noms, puis fournissez également une classe nommée `Debug` dans le même espace de noms. Plusieurs compilateurs requièrent que ces types soient qualifiés complets.

### <a name="namespaces-and-type-name-conflicts"></a>Conflits d’espaces de noms et de noms de types
 ❌ n’introduisez pas de noms de types génériques tels que `Element`, `Node`, `Log`et `Message`.

 Il y a une très grande probabilité que cela entraîne des conflits de noms de types dans les scénarios courants. Vous devez qualifier les noms de types génériques (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).

 Il existe des instructions spécifiques pour éviter les conflits de noms de types pour différentes catégories d’espaces de noms.

- **Espaces de noms du modèle d’application**

     Les espaces de noms appartenant à un modèle d’application unique sont souvent utilisés ensemble, mais ils ne sont jamais utilisés avec des espaces de noms d’autres modèles d’application. Par exemple, l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> est très rarement utilisé avec l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType>. Voici une liste de groupes d’espaces de noms de modèle d’application connus :

     `System.Windows*` `System.Web.UI*`

     ❌ n’attribuez pas le même nom aux types dans des espaces de noms dans un modèle d’application unique.

     Par exemple, n’ajoutez pas de type nommé `Page` à l’espace de noms <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, car l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType> contient déjà un type nommé `Page`.

- **Espaces de noms d’infrastructure**

     Ce groupe contient des espaces de noms rarement importés pendant le développement d’applications courantes. Par exemple, les espaces de noms `.Design` sont principalement utilisés lors du développement d’outils de programmation. Éviter les conflits avec les types de ces espaces de noms n’est pas critique.

- **Espaces de noms principaux**

     Les espaces de noms principaux incluent tous les espaces de noms `System`, à l’exclusion des espaces de noms des modèles d’application et des espaces de noms d’infrastructure. Les espaces de noms principaux incluent, entre autres, les `System`, les `System.IO`, les `System.Xml`et les `System.Net`.

     ❌ n’attribuez pas de noms de types qui seraient en conflit avec n’importe quel type dans les espaces de noms de base.

     Par exemple, n’utilisez jamais `Stream` comme nom de type. Il serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, un type très couramment utilisé.

- **Groupes d’espaces de noms technologiques**

     Cette catégorie comprend tous les espaces de noms ayant les mêmes deux premiers nœuds d’espace de noms `(<Company>.<Technology>*`), tels que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`. Il est important que les types appartenant à une même technologie n’entrent pas en conflit.

     ❌ n’attribuez pas de noms de types qui seraient en conflit avec d’autres types au sein d’une même technologie.

     ❌ n’introduisent pas de conflits de nom de type entre les types dans les espaces de noms technologiques et un espace de noms de modèle d’application (sauf si la technologie n’est pas destinée à être utilisée avec le modèle d’application).

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)

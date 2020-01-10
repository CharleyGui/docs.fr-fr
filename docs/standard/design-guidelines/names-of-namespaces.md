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
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709229"
---
# <a name="names-of-namespaces"></a>Noms d'espaces de noms
Comme pour les autres instructions d’affectation de noms, l’objectif de l’attribution de noms aux espaces de noms est de créer suffisamment de clarté pour le programmeur qui utilise l’infrastructure pour savoir immédiatement ce que le contenu de l’espace de noms est susceptible d’être. Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Voici quelques exemples :  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** faites précéder les noms d’espace de noms avec un nom de société pour empêcher les espaces de noms provenant de différentes sociétés de ne pas avoir le même nom.  
  
 **✓ DO** utiliser un nom de produit indépendant de la version stable au deuxième niveau d’un espace de noms.  
  
 **X DO NOT** utiliser des hiérarchies d’organisation comme base pour les noms dans les hiérarchies de l’espace de noms, étant donné que les noms de groupe au sein des entreprises ont tendance à être de courte durée de vie. Organiser la hiérarchie des espaces de noms autour des groupes de technologies associées.  
  
 **✓ DO** utilisent la casse Pascal et des composants de l’espace de noms distinct avec des périodes (par exemple, `Microsoft.Office.PowerPoint`). Si votre personnalisation utilise une casse qui n’est pas traditionnelle, vous devez suivre la casse définie par votre personnalisation, même si elle diffère de la casse normale des espaces de noms.  
  
 **✓ CONSIDER** à l’aide de noms au pluriel, le cas échéant.  
  
 Par exemple, utilisez `System.Collections` à la place de `System.Collection`. Toutefois, les noms et les acronymes sont des exceptions à cette règle. Par exemple, utilisez `System.IO` à la place de `System.IOs`.  
  
 **X DO NOT** utiliser le même nom pour un espace de noms et un type dans cet espace de noms.  
  
 Par exemple, n’utilisez pas `Debug` comme nom d’espace de noms, puis fournissez également une classe nommée `Debug` dans le même espace de noms. Plusieurs compilateurs requièrent que ces types soient qualifiés complets.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Conflits d’espaces de noms et de noms de types  
 **X DO NOT** présentent des noms de type générique comme `Element`, `Node`, `Log`, et `Message`.  
  
 Il y a une très grande probabilité que cela entraîne des conflits de noms de types dans les scénarios courants. Vous devez qualifier les noms de types génériques (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Il existe des instructions spécifiques pour éviter les conflits de noms de types pour différentes catégories d’espaces de noms.  
  
- **Espaces de noms du modèle d’application**  
  
     Les espaces de noms appartenant à un modèle d’application unique sont souvent utilisés ensemble, mais ils ne sont jamais utilisés avec des espaces de noms d’autres modèles d’application. Par exemple, l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> est très rarement utilisé avec l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType>. Voici une liste de groupes d’espaces de noms de modèle d’application connus :  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** donner le même nom aux types dans les espaces de noms dans un modèle d’application unique.  
  
     Par exemple, n’ajoutez pas de type nommé `Page` à l’espace de noms <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, car l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType> contient déjà un type nommé `Page`.  
  
- **Espaces de noms d’infrastructure**  
  
     Ce groupe contient des espaces de noms rarement importés pendant le développement d’applications courantes. Par exemple, les espaces de noms `.Design` sont principalement utilisés lors du développement d’outils de programmation. Éviter les conflits avec les types de ces espaces de noms n’est pas critique.  
  
- **Espaces de noms principaux**  
  
     Les espaces de noms principaux incluent tous les espaces de noms `System`, à l’exclusion des espaces de noms des modèles d’application et des espaces de noms d’infrastructure. Les espaces de noms principaux incluent, entre autres, les `System`, les `System.IO`, les `System.Xml`et les `System.Net`.  
  
     **X DO NOT** permettent de types de noms qui sont en conflit avec un type dans les espaces de noms de base.  
  
     Par exemple, n’utilisez jamais `Stream` comme nom de type. Il serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, un type très couramment utilisé.  
  
- **Groupes d’espaces de noms technologiques**  
  
     Cette catégorie comprend tous les espaces de noms ayant les mêmes deux premiers nœuds d’espace de noms `(<Company>.<Technology>*`), tels que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`. Il est important que les types appartenant à une même technologie n’entrent pas en conflit.  
  
     **X DO NOT** affecter des noms de type qui sont en conflit avec d’autres types au sein d’une seule technologie.  
  
     **X DO NOT** présentent des conflits de nom de type entre les types dans les espaces de noms de technologie et un espace de noms de modèle d’application (à moins que la technologie n’est pas destinée à être utilisée avec le modèle d’application).  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)

---
title: Règles d’affectation de noms (analyse du code)
description: En savoir plus sur les règles de nommage de l’analyse du code.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis rules, naming rules
- naming rules
- rules, naming
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 88e7ec6bc1051fa98c46696b2193a5d5912eb111
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586959"
---
# <a name="naming-rules"></a>Règles d’affectation des noms

Les règles d’affectation de noms prennent en charge l’adhésion aux conventions de nommage des règles de conception .NET.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1700 : Ne nommez pas les valeurs enum 'Reserved'](ca1700.md)|Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture.|
|[CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](ca1707.md)|Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). Cette règle vérifie les espaces de noms, types, membres et paramètres.|
|[CA1708 : Les identificateurs ne doivent pas différer uniquement par leur casse](ca1708.md)|Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci.|
|[CA1710 : Les identificateurs doivent être dotés d'un suffixe correct](ca1710.md)|Par Convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou des types dérivés de ces types, ont un suffixe associé à l’interface ou au type de base.|
|[CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](ca1711.md)|Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques. Les autres noms de types ne doivent pas utiliser ces suffixes réservés.|
|[CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](ca1712.md)|Les noms des membres de l’énumération n’ont pas le préfixe du nom de type, car les informations de type doivent être fournies par les outils de développement.|
|[CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After](ca1713.md)|Le nom d'un événement commence par « Before » ou « After ». Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions.|
|[CA1714 : Les noms des enums Flags doivent être au pluriel](ca1714.md)|Une énumération publique a l’attribut System. FlagsAttribute et son nom ne se termine pas par « s ». Les types marqués avec FlagsAttribute ont des noms au pluriel, car l’attribut indique qu’il est possible de spécifier plusieurs valeurs.|
|[CA1715 : Les identificateurs doivent être dotés d'un préfixe correct](ca1715.md)|Le nom d’une interface extérieurement visible ne commence pas par un « I » majuscule.  Le nom d’un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « T » majuscule.|
|[CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés](ca1716.md)|Un nom d'espace de noms ou un nom de type correspond à un mot clé réservé dans un langage de programmation. Les identificateurs des espaces de noms et des types ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime.|
|[CA1717 : Seuls les noms des enums FlagsAttribute doivent être au pluriel](ca1717.md)|Selon les conventions d'attribution de nom, un nom au pluriel pour une énumération indique que plusieurs valeurs de l'énumération peuvent être spécifiées simultanément.|
|[CA1720 : Les identificateurs ne doivent pas contenir de noms de types](ca1720.md)|Le nom d'un paramètre dans un membre extérieurement visible contient un nom de type de données, ou le nom d'un membre extérieurement visible contient un nom de type de données spécifique à une langue.|
|[CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get](ca1721.md)|Le nom d'un membre public ou protégé commence par « Get ». Sinon, il correspond au nom d'une propriété publique ou protégée. Les méthodes et propriétés « Get » doivent porter des noms distinguant clairement leur fonction.|
|[CA1724 : Les noms de types ne doivent pas être identiques aux espaces de noms](ca1724.md)|Les noms de types ne doivent pas correspondre aux noms des espaces de noms .NET. La violation de cette règle peut réduire l’utilisation de la bibliothèque.|
|[CA1725 : Les noms des paramètres doivent correspondre à la déclaration de base](ca1725.md)|La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode.|

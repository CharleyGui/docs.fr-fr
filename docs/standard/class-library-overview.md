---
title: Présentation des bibliothèques de classes .NET
description: En savoir plus sur la bibliothèque de classes .NET. Les API .NET incluent des classes, des interfaces, des délégués et des types de valeur pour fournir l’accès aux fonctionnalités du système.
ms.date: 02/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET], library overview
- .NET, library overview
- class objects value type
- naming conventions [.NET]
- types, .NET
- user-defined types
- Visual Basic, data types
- data types [.NET], C++
- Visual C#, data types
- libraries, .NET
- data types [.NET], F#
- System namespace
- F#, data types
- .NET, class library
- type system [.NET]
- data types [.NET]
- value types
- data types [.NET], Visual Basic
- Common Language Specification
- namespaces [.NET]
- floating point value type
- class library [.NET]
- CLS
- logical value type
- built-in types
- namespaces [.NET], about namespaces
- Visual C++, data types
- members [.NET], type
- data types [.NET], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
ms.openlocfilehash: 95dcbea6e0b3f2cd91bd6955a11ede7c9731caca
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687527"
---
# <a name="net-class-library-overview"></a>Présentation des bibliothèques de classes .NET

Les API .NET incluent des classes, des interfaces, des délégués et des types de valeur qui accélèrent et optimisent le processus de développement et fournissent l’accès aux fonctionnalités du système. Pour faciliter l'interopérabilité entre les langages, la plupart des types .NET sont conformes CLS (Common Language Specification) et peuvent, par conséquent, être utilisés à partir de n'importe quel langage de programmation dont le compilateur est conforme CLS.  
  
Les types .NET sont le fondement sur lequel les applications, composants et contrôles .NET sont construits. .NET comprend des types qui effectuent les fonctions suivantes :  
  
- Représenter les types de données de base et les exceptions.  
  
- Encapsuler les structures de données.  
  
- Effectuer les E/S.  
  
- Accéder aux informations concernant les types chargés.  
  
- Appelez les vérifications de sécurité .NET.  
  
- Fournir l'accès aux données, l'interface GUI riche côté client et l'interface GUI côté client contrôlée par le serveur.  
  
.NET fournit un ensemble complet d'interfaces, ainsi que des classes abstraites et concrètes (non abstraites). Vous pouvez utiliser les classes concrètes telles quelles ou, dans de nombreux cas, dériver vos propres classes à partir de celles-ci. Pour utiliser les fonctionnalités d’une interface, vous pouvez créer une classe qui implémente l’interface ou dériver une classe de l’une des classes .NET qui implémentent l’interface.  
  
## <a name="naming-conventions"></a>Conventions d’affectation de noms

 Les types .NET utilisent un schéma de nommage dans lequel les points indiquent une hiérarchie. Cette technique regroupe les types associés en espaces de noms de sorte qu'ils peuvent être recherchés et référencés plus facilement. La première partie du nom complet (jusqu'au point le plus à droite) constitue le nom de l'espace de noms. La dernière partie du nom est le nom du type. Par exemple, `System.Collections.Generic.List<T>` représente le type `List<T>`, qui appartient à l’espace de noms `System.Collections.Generic`. Les types dans <xref:System.Collections.Generic> peuvent être utilisés pour manipuler des collections génériques.  
  
 Ce modèle d’affectation de noms permet aux développeurs de bibliothèques qui étendent .NET de créer des groupes hiérarchiques de types et de les nommer de manière cohérente et informatif. Il permet également d'identifier clairement les types par leur nom complet (autrement dit, par leur espace de noms et nom de type) et d'empêcher les collisions de nom de type. Les développeurs de bibliothèques sont censés utiliser la convention suivante lors de l'affectation de noms aux nouveaux espaces de noms :  
  
 *NomSociété* . *NomTechnologie*  
  
 Par exemple, l’espace de noms `Microsoft.Word` est conforme à cette indication.  
  
 L’utilisation de modèles d’affectation de noms pour regrouper des types associés dans des espaces de noms est un moyen utile pour générer et documenter des bibliothèques de classes. Cependant, ce schéma d’affectation de noms n’a pas d’effet sur la visibilité, l’accès aux membres, l’héritage, la sécurité ou la liaison. Un espace de noms peut être partitionné en plusieurs assemblys et un seul assembly peut contenir des types provenant de plusieurs espaces de noms. L'assembly fournit la structure formelle pour le versioning, le déploiement, la sécurité, le chargement et la visibilité dans le Common Language Runtime.  
  
 Pour plus d’informations sur les espaces de noms et les noms des types, consultez [Système de type commun (CTS, Common Type System)](base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>System (espace de noms)

 L'espace de noms <xref:System> est l'espace de noms racine pour les types fondamentaux dans .NET. Cet espace de noms comprend les classes qui représentent les types de données de base utilisés par toutes les applications : <xref:System.Object> (racine de la hiérarchie d'héritage), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>, et ainsi de suite. Nombre de ces types correspondent aux types de données primitifs que votre langage de programmation utilise. Quand vous écrivez du code à l’aide de types .NET, vous pouvez utiliser le mot clé correspondant de votre langage quand un type de données de base .NET est attendu.  
  
 Le tableau suivant énumère les types de base fournis par .NET, décrit brièvement chaque type et indique le type correspondant en Visual Basic, C#, C++ et F#.  
  
|Category|Nom de classe|Description|Type de données Visual Basic|Type de données C#|Type de données C++/CLI|Type de données F#|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Integer|<xref:System.Byte>|Entier non signé 8 bits.|**Byte**|**byte**|**unsigned char**|**byte**|  
||<xref:System.SByte>|Entier signé 8 bits.<br /><br /> Non conforme CLS.|**SByte**|**sbyte**|**char**<br /> -ou-<br /> **signed** **char**|**sbyte**|  
||<xref:System.Int16>|Entier signé 16 bits.|**Résumé**|**short**|**short**|**int16**|  
||<xref:System.Int32>|Entier signé 32 bits.|**Integer**|**int**|**int**<br /><br /> -ou-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|Entier signé 64 bits.|**Long**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|Entier non signé 16 bits.<br /><br /> Non conforme CLS.|**UShort**|**ushort**|**unsigned short**|**UInt16**|  
||<xref:System.UInt32>|Entier non signé 32 bits.<br /><br /> Non conforme CLS.|**UInteger**|**uint**|**nombre entier non signé**<br /> -ou-<br /> **unsigned long**|**uint32**|  
||<xref:System.UInt64>|Entier 64 bits non signé.<br /><br /> Non conforme CLS.|**Correspondante**|**ulong**|**unsigned __int64**|**uint64**|  
|Virgule flottante|<xref:System.Single>|Nombre à virgule flottante (32 bits) simple précision.|**Unique**|**float**|**float**|**float32**<br> or<br>**single**|  
||<xref:System.Double>|Nombre à virgule flottante (64 bits) double précision.|**Double**|**double**|**double**|**float**<br> or <br> **double**|  
|Logique|<xref:System.Boolean>|Valeur booléenne (true ou false).|**Booléen**|**bool**|**bool**|**bool**|  
|Autres|<xref:System.Char>|Caractère Unicode (16 bits).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Valeur décimale (128 bits).|**Décimal**|**decimal**|**Décimal**|**decimal**|  
||<xref:System.IntPtr>|Entier signé dont la taille dépend de la plateforme sous-jacente (valeur 32 bits sur une plateforme 32 bits et valeur 64 bits sur une plateforme 64 bits).|**IntPtr**<br /><br /> Pas de type intégré.|**IntPtr**<br /><br /> Pas de type intégré.|**IntPtr**<br /><br /> Pas de type intégré.|**unativeint**|  
||<xref:System.UIntPtr>|Entier non signé dont la taille dépend de la plateforme sous-jacente (valeur 32 bits sur une plateforme 32 bits et valeur 64 bits sur une plateforme 64 bits).<br /><br /> Non conforme CLS.|**UIntPtr**<br /><br /> Pas de type intégré.|**UIntPtr**<br /><br /> Pas de type intégré.|**UIntPtr**<br /><br /> Pas de type intégré.|**unativeint**|  
||<xref:System.Object>|Racine de la hiérarchie d'objet.|**Object**|**object**|**Objet ^**|**obj**|  
||<xref:System.String>|Chaîne immuable à longueur fixe de caractères Unicode.|**Chaîne**|**string**|**Chaîne ^**|**string**|  
  
 En plus des types de données de base, l'espace de noms <xref:System> contient plus de 100 classes, de celles qui gèrent les exceptions à celles qui traitent des principaux concepts relatifs au runtime, tels que les domaines d'application et le « garbage collector ». L'espace de noms <xref:System> contient également de nombreux espaces de noms de deuxième niveau.  
  
 Pour plus d’informations sur les espaces de noms, utilisez le [Navigateur d’API .NET](../../api/index.md) pour parcourir la bibliothèque de classes .NET. La documentation de référence sur les API fournit des informations sur chaque espace de noms, ses types et chacun de ses membres.  
  
## <a name="see-also"></a>Voir aussi

- [Système de type commun](base-types/common-type-system.md)
- [Navigateur d’API .NET](../../api/index.md)
- [Vue d'ensemble](../framework/get-started/overview.md)

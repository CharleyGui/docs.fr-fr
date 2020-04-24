---
title: Attributs (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 0379bb76cf18ff836bd14aafb9cb97c30aee8ec7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645488"
---
# <a name="attributes-c"></a>Attributs (C#)

Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.). Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*. Pour plus d’informations, consultez [Réflexion (C#)](../reflection.md).

Les attributs ont les propriétés suivantes :

- Les attributs ajoutent des métadonnées à un programme. Les *métadonnées* sont des informations sur les types définis dans un programme. Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly. Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire. Pour plus d’informations, consultez [Création d’attributs personnalisés (C#)](creating-custom-attributes.md).
- Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.
- Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.
- Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion. Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Utilisation des attributs

Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide. En C#, vous spécifiez un attribut en plaçant son nom entre crochets ([]) au-dessus de la déclaration de l’entité à laquelle il s’applique.

Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme dans l’exemple suivant :

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Plusieurs attributs peuvent être placés dans une déclaration comme dans l’exemple suivant :

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée. <xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments dans les bibliothèques .NET. Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code. Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans la bibliothèque de classes .NET Framework.

### <a name="attribute-parameters"></a>Paramètres d’attributs

Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés. Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peut pas être omis. Les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre. Les paramètres positionnels sont spécifiés en premier. Par exemple, ces trois attributs sont équivalents :

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés. Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis. Les paramètres positionnels correspondent aux paramètres du constructeur d’attribut. Les paramètres nommés ou facultatifs correspondent aux propriétés ou champs de l’attribut. Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.

### <a name="attribute-targets"></a>Cibles d’attribut

La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut. Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier. Par défaut, un attribut s’applique à l’élément qui le suit. Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.

Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :

```csharp
[target : attribute-list]
```

La liste des valeurs `target` possibles est présentée dans le tableau suivant.

|Valeur cible|S’applique à|
|------------------|----------------|
|`assembly`|Assembly entier|
|`module`|Module d’assembly actuel|
|`field`|Champ dans une classe ou un struct|
|`event`|Événement|
|`method`|Méthode ou accesseurs de propriété `get` et `set`|
|`param`|Paramètres de méthode ou paramètres d’accesseur de propriété `set`|
|`property`|Propriété|
|`return`|Valeur de retour d’une méthode, indexeur de propriété ou accesseur de propriété `get`|
|`type`|Struct, classe, interface, énumération ou délégué|

Vous devez spécifier la valeur cible de `field` pour appliquer un attribut au champ de stockage créé pour une [propriété implémentée automatiquement](../../../properties.md).

L’exemple suivant montre comment appliquer des attributs à des modules et assemblys. Pour plus d’informations, consultez [Attributs courants (C#)](../../../language-reference/attributes/global.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

L’exemple suivant montre comment appliquer des attributs à des méthodes, des paramètres de méthode et des valeurs de retour de méthode en C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Quelle que soit la cible sur laquelle `ValidatedContract` est défini comme étant valide, la cible `return` doit être spécifiée, même si `ValidatedContract` a été défini pour s’appliquer seulement aux valeurs de retour. En d’autres termes, le compilateur n’utilise pas les informations `AttributeUsage` pour résoudre les cibles d’attribut ambiguës. Pour plus d’informations, consultez [AttributeUsage (C#)](../../../language-reference/attributes/general.md).

## <a name="common-uses-for-attributes"></a>Utilisations courantes des attributs

La liste suivante comprend certaines des utilisations courantes des attributs dans le code :

- Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP. Pour plus d’informations, consultez <xref:System.Web.Services.WebMethodAttribute>.
- Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif. Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Décrire les propriétés COM des classes, méthodes et interfaces.
- Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.
- Décrire un assembly : titre, version, description ou marque.
- Décrire les membres d’une classe à sérialiser à des fins de persistance.
- Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.
- Décrire les exigences de sécurité des méthodes.
- Spécifier les caractéristiques employées pour appliquer la sécurité.
- Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.
- Obtenir des informations sur l’appelant d’une méthode.

## <a name="related-sections"></a>Sections connexes

Pour plus d'informations, consultez les pages suivantes :

- [Création d’attributs personnalisés (C#)](creating-custom-attributes.md)  
- [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md)  
- [Comment créer un syndicat C/CMD en utilisant des attributs (C)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Attributs courants (C#)](../../../language-reference/attributes/global.md)  
- [Informations relatives à l’appelant (C#)](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../../index.md)
- [Réflexion (C#)](../reflection.md)
- [Attributs](../../../../standard/attributes/index.md)
- [Utilisation d’attributs en C #](../../../tutorials/attributes.md)

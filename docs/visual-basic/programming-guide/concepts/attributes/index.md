---
title: Vue d’ensemble des attributs
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: a0a080d44796289cc3562803c84ec915dcedd314
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400705"
---
# <a name="attributes-overview-visual-basic"></a>Vue d’ensemble des attributs (Visual Basic)

Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.). Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*. Pour plus d’informations, consultez la page [Réflexion (Visual Basic)](../reflection.md).

Les attributs ont les propriétés suivantes :

- Les attributs ajoutent des métadonnées à un programme. Les *métadonnées* sont des informations sur les types définis dans un programme. Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly. Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire. Pour plus d’informations, consultez la page [Création d’attributs personnalisés (Visual Basic)](creating-custom-attributes.md).

- Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.

- Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.

- Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion. Pour plus d’informations, consultez la page [Accéder à des attributs grâce à la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Utilisation d'attributs

Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide. Dans Visual Basic, un attribut est placé entre crochets pointus ( \< > ). Il doit apparaître immédiatement avant l’élément auquel il s’applique, sur la même ligne.

Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme suit :

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

Plusieurs attributs peuvent être placés dans une déclaration :

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée. <xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments de .NET Framework. Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code. Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans .NET Framework.

### <a name="attribute-parameters"></a>Paramètres d’attributs

Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés. Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peuvent pas être omis ; les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre. Les paramètres positionnels sont spécifiés en premier. Par exemple, ces trois attributs sont équivalents :

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés. Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis. Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.

### <a name="attribute-targets"></a>Cibles d'attribut

La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut. Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier. Par défaut, un attribut s’applique à l’élément qu’il précède. Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.

Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :

```vb
<target : attribute-list>
```

La liste des valeurs `target` possibles est présentée dans le tableau suivant.

|Valeur cible|S’applique à|
|------------------|----------------|
|`assembly`|Assembly entier|
|`module`|Module d’assembly actif (différent d’un module Visual Basic)|

 L’exemple suivant montre comment appliquer des attributs à des modules et assemblys. Pour plus d’informations, consultez la page [Attributs courants (Visual Basic)](common-attributes.md).

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

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

Pour plus d'informations, voir :

- [Créer des attributs personnalisés (Visual Basic)](creating-custom-attributes.md)

- [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md)

- [Guide pratique : créer une union C/C++ à l’aide d’attributs (Visual Basic)](how-to-create-a-c-cpp-union-by-using-attributes.md)

- [Attributs courants (Visual Basic)](common-attributes.md)

- [Informations relatives à l’appelant (Visual Basic)](../caller-information.md)

## <a name="see-also"></a>Voir aussi

- [Guide de programmation Visual Basic](../../index.md)
- [Réflexion (Visual Basic)](../reflection.md)
- [Attributs](../../../../standard/attributes/index.md)

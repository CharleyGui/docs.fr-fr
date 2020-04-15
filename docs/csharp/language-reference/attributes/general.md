---
title: 'Attributs réservés CMD : Conditionnel, obsolète, AttributUsage'
ms.date: 04/09/2020
description: Ces attributs sont interprétés par le compilateur pour affecter le code généré par le compilateur
ms.openlocfilehash: ca3b76387de2a57380d6eb0848991d979a558662
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389869"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Attributs réservés: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute

Ces attributs peuvent être appliqués à des éléments de votre code. Ils ajoutent un sens sémantique à ces éléments. Le compilateur utilise ces significations sémantiques pour modifier sa sortie et signaler les erreurs possibles des développeurs utilisant votre code.

## <a name="conditional-attribute"></a>Attribut `Conditional`

Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement. L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.

Dans l’exemple `Conditional` suivant, est appliqué à une méthode pour activer ou désactiver l’affichage d’informations diagnostiques spécifiques au programme :

::::::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

Si `TRACE_ON` l’identifiant n’est pas défini, la sortie de trace n’est pas affichée. Explorez par vous-même dans la fenêtre interactive.

L’attribut `Conditional` est souvent `DEBUG` utilisé avec l’identifiant pour activer les traces et les caractéristiques d’enregistrement pour les constructions de débogé, mais pas dans les versions, comme le montre l’exemple suivant:

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Lorsqu’une méthode marquée conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis. Si le symbole est défini, l’appel est inclus ; sinon, il est omis. Une méthode conditionnelle doit être une méthode dans une `void` déclaration de classe ou de struct et doit avoir un type de retour. L’utilisation `Conditional` est plus propre, plus élégante et moins `#if…#endif` sujette aux erreurs que d’enfermer des méthodes à l’intérieur des blocs.

Si une méthode `Conditional` a plusieurs attributs, un appel à la méthode est inclus si un ou plusieurs symboles conditionnels sont définis (les symboles sont logiquement reliés entre eux par l’utilisation de l’opérateur DE la RO). Dans l’exemple suivant, `A` la `B` présence de l’un ou l’autre ou les résultats dans un appel de méthode :

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Utilisation `Conditional` avec des classes d’attributs

L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs. Dans l’exemple suivant, `Documentation` l’attribut personnalisé n’ajoutera des informations aux métadonnées que si `DEBUG` elle est définie.

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>Attribut `Obsolete`

L’attribut `Obsolete` marque un élément de code comme n’étant plus recommandé pour une utilisation. L’utilisation d’une entité marquée obsolète génère un avertissement ou une erreur. `Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs. `Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.

Dans l’exemple `Obsolete` suivant, l’attribut est appliqué à la classe `A` et à la méthode `B.OldMethod`. Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement. Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur. Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :

::::::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

La chaîne fournie comme premier argument au constructeur d’attributs sera affichée dans le cadre de l’avertissement ou de l’erreur. Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe. L’attribut `Obsolete` peut être utilisé sans arguments, mais y compris une explication ce qu’il faut utiliser à la place est recommandé.

## <a name="attributeusage-attribute"></a>Attribut `AttributeUsage`

L’attribut `AttributeUsage` détermine comment une classe d’attributs personnalisée peut être utilisée. <xref:System.AttributeUsageAttribute> est un attribut que vous appliquez à des définitions d’attribut personnalisé. L’attribut `AttributeUsage` vous permet de contrôler :

- À quels éléments de programme les attributs peuvent être appliqués. Sauf si vous en limitez l’utilisation, un attribut peut être appliqué aux éléments de programme suivants :
  - assembly
  - module
  - field
  - event
  - method
  - param
  - propriété
  - return
  - type
- Si un attribut peut être appliqué plusieurs fois à un même élément de programme.
- Si les attributs sont hérités dans les classes dérivées.

L’exemple suivant montre des paramètres par défaut quand ils sont appliqués explicitement :

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

Dans cet exemple, la classe `NewAttribute` peut être appliquée à n’importe quel élément de programme pris en charge. Elle ne peut cependant être appliquée qu’une seule fois à chaque entité. L’attribut est hérité par les classes dérivées quand il est appliqué à une classe de base.

Les arguments <xref:System.AttributeUsageAttribute.AllowMultiple> et <xref:System.AttributeUsageAttribute.Inherited> étant facultatifs, le code suivant a le même effet :

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

Le premier argument <xref:System.AttributeUsageAttribute> doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>. Vous pouvez lier ensemble plusieurs types de cibles avec l’opérateur OR, comme dans l’exemple suivant :

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

À compter de C# 7.3, les attributs peuvent être appliqués à la propriété ou au champ de stockage pour une propriété implémentée automatiquement. L’attribut s’applique à la propriété, sauf si vous spécifiez le spécificateur `field` sur l’attribut. Les deux cas sont illustrés dans l’exemple suivant :

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

Si l’argument <xref:System.AttributeUsageAttribute.AllowMultiple> est défini sur `true`, l’attribut résultant peut être appliqué plusieurs fois à une même entité, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

Dans ce cas, `MultiUseAttribute` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`. Les deux formats indiqués pour appliquer plusieurs attributs sont valides.

Si <xref:System.AttributeUsageAttribute.Inherited> est `false`, l’attribut n’est pas hérité par les classes dérivées d’une classe avec attributs. Par exemple :

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

Dans ce cas, `NonInheritedAttribute` n’est pas appliqué à `DClass` via l’héritage.

## <a name="see-also"></a>Voir aussi

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Attributs](../../../standard/attributes/index.md)
- [Réflexion](../../programming-guide/concepts/reflection.md)

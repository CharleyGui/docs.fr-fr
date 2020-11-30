---
title: 'Attributs réservés C# : Conditional, Obsolete, AttributeUsage'
ms.date: 04/09/2020
description: Ces attributs sont interprétés par le compilateur pour affecter le code généré par le compilateur.
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021764"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Attributs réservés : ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute

Ces attributs peuvent être appliqués aux éléments de votre code. Ils ajoutent une signification sémantique à ces éléments. Le compilateur utilise ces significations sémantiques pour modifier sa sortie et signaler les erreurs possibles par les développeurs qui utilisent votre code.

## <a name="conditional-attribute"></a>Attribut `Conditional`

Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement. L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.

Dans l’exemple suivant, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage des informations de diagnostic spécifiques au programme :

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

Si l' `TRACE_ON` identificateur n’est pas défini, la sortie de trace n’est pas affichée. Explorez par vous-même dans la fenêtre interactive.

L' `Conditional` attribut est souvent utilisé avec l' `DEBUG` identificateur pour activer les fonctionnalités de suivi et de journalisation pour les versions Debug, mais pas dans les versions release, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Quand une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis. Si le symbole est défini, l’appel est inclus ; sinon, il est omis. Une méthode conditionnelle doit être une méthode dans une déclaration de classe ou de struct et doit avoir un `void` type de retour. L’utilisation de `Conditional` est plus propre, plus élégante et moins sujette aux erreurs que les méthodes englobantes à l’intérieur des `#if…#endif` blocs.

Si une méthode a plusieurs `Conditional` attributs, un appel à la méthode est inclus si un ou plusieurs symboles conditionnels sont définis (les symboles sont logiquement liés ensemble à l’aide de l’opérateur or). Dans l’exemple suivant, la présence d' `A` un ou de `B` résultats dans un appel de méthode :

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Utiliser `Conditional` avec des classes d’attributs

L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs. Dans l’exemple suivant, l’attribut personnalisé `Documentation` ajoute uniquement des informations aux métadonnées si `DEBUG` est défini.

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>Attribut `Obsolete`

L' `Obsolete` attribut marque un élément de code comme n’est plus recommandé pour une utilisation. L’utilisation d’une entité marquée comme obsolète génère un avertissement ou une erreur. `Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs. `Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.

Dans l’exemple suivant, l' `Obsolete` attribut est appliqué à la classe `A` et à la méthode `B.OldMethod` . Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement. Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur. Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

La chaîne fournie comme premier argument au constructeur d’attribut sera affichée dans le cadre de l’avertissement ou de l’erreur. Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe. L' `Obsolete` attribut peut être utilisé sans arguments, mais il est recommandé d’utiliser à la place une explication.

## <a name="attributeusage-attribute"></a>Attribut `AttributeUsage`

L' `AttributeUsage` attribut détermine la manière dont une classe d’attributs personnalisés peut être utilisée. <xref:System.AttributeUsageAttribute> est un attribut que vous appliquez à des définitions d’attribut personnalisé. L’attribut `AttributeUsage` vous permet de contrôler :

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

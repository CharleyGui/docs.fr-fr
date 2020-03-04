---
title: Analyseurs de .NET Framework-.NET
description: Découvrez comment utiliser les analyseurs de .NET Framework dans le package des analyseurs de .NET Framework pour rechercher et résoudre les problèmes de sécurité
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155995"
---
# <a name="the-net-framework-analyzer"></a>L’analyseur .NET Framework

Vous pouvez utiliser l’Analyseur .NET Framework pour rechercher les problèmes potentiels dans votre code d’application basé sur .NET Framework. Cet analyseur recherche les problèmes potentiels et suggère des correctifs pour les résoudre.

L’analyseur s’exécute de façon interactive dans Visual Studio au fil de l’écriture du code ou dans le cadre d’une build CI. Il est recommandé d’ajouter l’analyseur à votre projet dès que possible dans votre développement. Plus tôt vous trouvez les problèmes potentiels dans votre code, plus ils sont faciles à corriger. Cependant, vous pouvez l’ajouter à tout moment au cours du cycle de développement. Il détecte les problèmes dans le code existant et signale les problèmes au fil de votre développement.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Installation et configuration de l’Analyseur .NET Framework

Les analyseurs de .NET Framework doivent être installés en tant que package NuGet sur chaque projet où vous souhaitez qu’ils s’exécutent. Il suffit qu’un seul développeur les ajoute au projet. Le package de l’analyseur est une dépendance de projet et il s’exécute sur la machine de chaque développeur une fois qu’il dispose de la solution mise à jour.

L’Analyseur .NET Framework est livré dans le package NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/). Ce package fournit seulement les analyseurs spécifiques à .NET Framework, qui comprend des analyseurs de sécurité. Dans la plupart des cas, vous allez utiliser le package NuGet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).
Le package d’agrégation FxCopAnalyzers contient tous les analyseurs de framework inclus dans le package Framework.Analyzers, ainsi que les analyseurs suivants :

- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers) : fournit des indications générales et des conseils pour les API .NET Standard.
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers) : fournit des analyseurs spécifiques aux API .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers) : fournit des conseils pour le texte inclus en tant que code, notamment les commentaires.

Pour l’installer, cliquez avec le bouton droit sur le projet et sélectionnez « Gérer les dépendances ».
Dans l’Explorateur NuGet, recherchez « NetFramework Analyzer » ou, si vous préférez, « Fx Cop Analyzerx ». Installez la dernière version stable dans tous les projets de votre solution.

## <a name="using-the-net-framework-analyzer"></a>Utilisation de l’Analyseur .NET Framework

Une fois le package NuGet installé, générez votre solution. L’analyseur signale les éventuels problèmes qu’il trouve dans votre code base. Les problèmes sont signalés sous forme d’avertissements dans la fenêtre Liste d’erreurs de Visual Studio, comme le montre l’image suivante :

![problèmes signalés par l’analyseur d’infrastructure](./media/framework-analyzers-2.png)

Au fil de l’écriture du code, vous voyez des marques ondulées sous les problèmes potentiels de votre code.
Placez le curseur sur un problème pour voir plus d’informations sur celui-ci, ainsi que des suggestions pour une correction possible, comme le montre l’image suivante :

![rapport interactif des problèmes détectés par l’Analyseur de framework](./media/framework-analyzers-1.png)

Les analyseurs examinent le code de votre solution et vous fournissent une liste d’avertissements pour ces problèmes :

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058 : Les types ne doivent pas étendre certains types de base

Vous ne devez rien dériver directement d’un petit nombre de types du .NET Framework.

**Catégorie :** Conception

**Gravité :** Avertissement

Informations supplémentaires : [CA1058 : Les types ne doivent pas étendre certains types de base](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153 : Ne pas intercepter des exceptions d’état endommagé

L’interception des exceptions d’état endommagé pourrait masquer des erreurs (comme des violations d’accès), aboutissant à un état d’exécution incohérent ou facilitant la compromission d’un système par des attaquants. Au lieu de cela, il faut intercepter et gérer un ensemble de types d’exception plus spécifiques, ou lever à nouveau l’exception.

**Catégorie :** Sécurité

**Gravité :** Avertissement

Informations supplémentaires : [## CA2153 : Ne pas intercepter les exceptions d’état endommagé](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229 : Implémentez des constructeurs de sérialisation

L’analyseur génère cet avertissement quand vous créez un type qui implémente l’interface <xref:System.Runtime.Serialization.ISerializable>, mais ne définit pas le constructeur de sérialisation nécessaire. Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé. Le constructeur de sérialisation a la signature suivante :

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**Catégorie :** Utilisation

**Gravité :** Avertissement

Informations supplémentaires : [CA2229 : Implémentez des constructeurs de sérialisation](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235 : Marquez tous les champs non sérialisés

Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable. Vous devez marquer explicitement ce champ avec <xref:System.NonSerializedAttribute> pour résoudre cet avertissement.

**Catégorie :** Utilisation

**Gravité :** Avertissement

Informations supplémentaires : [CA2235 : Marquez tous les champs non sérialisables](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237 : Marquez les types ISerializable comme étant sérialisables

Pour être reconnus par le Common Language Runtime comme étant sérialisables, les types doivent être marqués avec l’attribut <xref:System.SerializableAttribute>, même s’ils utilisent une routine de sérialisation personnalisée en implémentant l’interface <xref:System.Runtime.Serialization.ISerializable>.

**Catégorie :** Utilisation

**Gravité :** Avertissement

Informations supplémentaires : [CA2237 : Marquez les types ISerializable comme étant sérialisables](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075 : Traitement du DTD non sécurisé dans XML

Si vous utilisez des instances de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> non sécurisées ou référencez des sources d’entités externes, l’analyseur peut accepter une entrée non fiable et divulguer des informations sensibles à des personnes malveillantes.  

**Catégorie :** Sécurité

**Gravité :** Avertissement

Informations supplémentaires : [A3075 : Traitement du DTD non sécurisé dans XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles

Les algorithmes de chiffrement se dégradent au fil du temps, car les attaques deviennent plus sophistiquées. Selon le type et l’application de cet algorithme de chiffrement, une dégradation progressive de sa force de chiffrement peut permettre aux attaquants de lire des messages chiffrés, de falsifier des messages chiffrés, de falsifier des signatures numériques, de falsifier du contenu haché ou de compromettre les systèmes de chiffrement basés sur cet algorithme. Pour le chiffrement, utilisez un algorithme AES (AES-256, AES-192 et AES-128 sont acceptables) avec une longueur de clé supérieure ou égale à 128 bits. Pour le hachage, utilisez une fonction de hachage de la famille SHA-2, comme SHA-2 512, SHA-2 384 ou SHA-2 256.

**Catégorie :** Sécurité

**Gravité :** Avertissement

Informations supplémentaires : [CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 : N’utilisez pas les algorithmes de chiffrement cassés

Il existe une attaque qui permet de casser cet algorithme par voie informatique. Ceci permet aux attaquants de passer outre les garanties en matière de chiffrement qu’il doit normalement fournir. Selon le type et l’application de cet algorithme de chiffrement, ceci peut permettre aux attaquants de lire des messages chiffrés, de falsifier des messages chiffrés, de falsifier des signatures numériques, de falsifier du contenu haché ou de compromettre les systèmes de chiffrement basés sur cet algorithme. Pour le chiffrement, utilisez un algorithme AES (AES-256, AES-192 et AES-128 sont acceptables) avec une longueur de clé supérieure ou égale à 128 bits. Pour le hachage, utilisez une fonction de hachage de la famille SHA-2, comme SHA512, SHA384 ou SHA256. Pour les signatures numériques, utilisez RSA avec une longueur de clé supérieure ou égale à 2048 bits, ou ECDSA avec une longueur de clé supérieure ou égale à 256 bits.

**Catégorie :** Sécurité

**Gravité :** Avertissement

Informations supplémentaires : [CA5351 : N’utilisez pas d’algorithmes de chiffrement cassés](/visualstudio/code-quality/ca5351)

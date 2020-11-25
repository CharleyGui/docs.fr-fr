---
title: 'Modification avec rupture : valeur FeedbackSize par défaut pour les instances créées par TripleDES. Create Changed'
description: Découvrez la modification avec rupture dans .NET 5,0 où la valeur par défaut de la propriété FeedbackSize sur l’instance TripleDES retournée par TripleDES. Create () est passée de 64 à 8.
ms.date: 10/16/2020
ms.openlocfilehash: 4179da17bf2e5cc5fcc7d64d83ba92119f912042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761130"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a>Valeur FeedbackSize par défaut pour les instances créées par TripleDES. Create Changed

La valeur par défaut de la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> propriété sur l' <xref:System.Security.Cryptography.TripleDES> instance retournée de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> est passée de 64 à 8 pour faciliter la migration à partir de .NET Framework. Cette propriété, sauf si elle est utilisée directement dans le code de l’appelant, est utilisée uniquement lorsque la <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriété est <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .

La prise en charge du <xref:System.Security.Cryptography.CipherMode.CFB> mode a été ajoutée à .net pour la version 5,0 RC1. par conséquent, seules les applications .net 5,0 RC1 et .net 5,0 RC2 doivent être affectées par cette modification.

## <a name="change-description"></a>Description de la modification

Dans .NET Core et les versions antérieures à la version préliminaire de .NET 5,0, `TripleDES.Create().FeedbackSize` a une valeur par défaut de 64. À partir de la version RTM de .NET 5,0, `TripleDES.Create().FeedbackSize` a une valeur par défaut de 8.

## <a name="reason-for-change"></a>Motif de modification

Dans .NET Framework, la <xref:System.Security.Cryptography.TripleDES> classe de base a par défaut la valeur <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 64, mais la <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe remplace la valeur par défaut par 8. Lorsque la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété a été introduite dans .net core dans la version 2,0, ce même comportement a été préservé. Toutefois, dans .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> retourne une instance de <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , donc la valeur par défaut de la fabrique d’algorithme est 8. Pour .NET Core et .NET 5 +, la fabrique d’algorithmes retourne une implémentation non publique, qui, jusqu’à présent, avait une valeur par défaut de 64.

La modification de la <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> valeur de la classe d’implémentation à 8 permet aux applications écrites pour .NET Framework qui ont spécifié le mode de chiffrement <xref:System.Security.Cryptography.CipherMode.CFB> , mais n’ont pas explicitement assigné la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété, pour continuer à fonctionner sur .net 5.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Les applications qui chiffrent ou déchiffrent les données dans les versions RC1 ou RC2 de .NET 5,0 le font avec CFB64, quand les conditions suivantes sont remplies :

- Avec une <xref:System.Security.Cryptography.TripleDES> instance de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .
- À l’aide de la valeur par défaut pour <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .
- Avec la <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriété définie sur <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .

Pour conserver ce comportement, assignez la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété à `64` .

Toutes les `TripleDES` implémentations n’utilisent pas la même valeur par défaut pour <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> . Si vous utilisez le <xref:System.Security.Cryptography.CipherMode.CFB> mode de chiffrement sur les <xref:System.Security.Cryptography.TripleDES> instances, nous vous recommandons de toujours assigner explicitement la valeur de la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété.

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->

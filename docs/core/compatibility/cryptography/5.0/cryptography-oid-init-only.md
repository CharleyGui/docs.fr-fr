---
title: 'Modification avec rupture : Cryptography. OID est fonctionnellement init-only'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où les accesseurs set de propriété sur la classe Cryptography. OID lèvent désormais une exception si vous tentez de modifier une valeur.
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760884"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>System. Security. Cryptography. OID est fonctionnellement init-only

La <xref:System.Security.Cryptography.Oid?displayProperty=fullName> classe, qui est utilisée pour représenter les valeurs de l’identificateur d’objet ASN. 1 et leurs noms « conviviaux », était auparavant complètement mutable. Cette mutabilité a souvent été négligée ou est apparue comme une surprise. Les accesseurs set de propriété lèvent désormais une <xref:System.PlatformNotSupportedException> lorsque vous tentez de modifier la valeur une fois qu’elle a déjà été assignée.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes, les accesseurs set de propriété on <xref:System.Security.Cryptography.Oid> peuvent être utilisés pour modifier la valeur des <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> Propriétés et.

Dans .NET 5,0 et versions ultérieures, les accesseurs set de propriété ne peuvent être utilisés que pour initialiser la valeur. Une fois que la propriété a une valeur, qu’il s’agisse d’un constructeur ou d’un appel précédent à la méthode setter de propriété, la méthode setter de la propriété lève toujours une exception <xref:System.PlatformNotSupportedException> .

## <a name="reason-for-change"></a>Motif de modification

Cette modification permet de réutiliser des <xref:System.Security.Cryptography.Oid> objets dans le cadre de valeurs de retour dans les API publiques pour réduire les profils d’allocation d’objets. Cela évite d’avoir à créer des copies « défensives » temporaires lorsque les <xref:System.Security.Cryptography.Oid> valeurs sont utilisées comme entrées.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Évitez d’utiliser les <xref:System.Security.Cryptography.Oid> accesseurs set de propriété autres que pour l’initialisation d’objet. Pour représenter une nouvelle valeur, utilisez une nouvelle instance au lieu de modifier la valeur d’un objet existant.

## <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->

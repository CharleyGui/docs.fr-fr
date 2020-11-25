---
title: 'Modification avec rupture : reconnaissance URI de chemins d’accès UNC sur UNIX'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où la classe Uri reconnaît désormais les chaînes qui commencent par deux barres obliques comme chemins d’accès UNC sur UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760875"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a>Reconnaissance d’URI de chemins d’accès UNC sur UNIX

La <xref:System.Uri> classe reconnaît maintenant les chaînes qui commencent par deux barres obliques ( `//` ) en tant que chemins d’accès UNC (Universal Naming Convention) sur les systèmes d’exploitation UNIX. Cette modification rend le comportement de ces chaînes cohérent sur toutes les plateformes.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par deux barres obliques, par exemple, `//contoso` sous la forme de chemins de fichiers absolus sur les systèmes d’exploitation UNIX. Toutefois, sous Windows, ces chaînes sont reconnues comme des chemins d’accès UNC.

À compter de .NET 5,0, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par deux barres obliques comme chemins d’accès UNC sur toutes les plateformes, y compris UNIX. En outre, les propriétés se comportent selon la sémantique UNC :

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> retourne `true`.
- Les barres obliques inverses dans le chemin d’accès sont remplacées par des barres obliques. Par exemple, `//first\second` devient `//first/second`.
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> n’encode pas les caractères en pourcentage. Par exemple, `//first/\uFFF0` n’est *pas* converti en `//first/%EF%BF%B0` .

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

## <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->

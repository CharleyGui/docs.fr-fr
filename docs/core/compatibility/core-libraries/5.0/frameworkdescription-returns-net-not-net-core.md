---
title: 'Modification avec rupture : la valeur de FrameworkDescription est .NET au lieu de .NET Core'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où RuntimeInformation. FrameworkDescription retourne désormais « .NET » au lieu de « .NET Core ».
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761069"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>La valeur de FrameworkDescription est .NET au lieu de .NET Core

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne désormais « .NET » au lieu de « .NET Core ».

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net core » dans le cadre de la chaîne de description, par exemple `.NET Core 3.1.1` .

À compter de .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net » dans le cadre de la chaîne de description, par exemple `.NET 5.0.0` .

## <a name="reason-for-change"></a>Motif de modification

Avec .NET 5, `netcoreapp` est remplacé par `net` comme moniker de Framework cible courts. Pour des fins de cohérence, la description de l’infrastructure a également été mise à jour. La modification est cosmétique, car `FrameworkName` n’est pas encodé ailleurs que dans la <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriété.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui recherche « .NET Core » dans la chaîne retournée par <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

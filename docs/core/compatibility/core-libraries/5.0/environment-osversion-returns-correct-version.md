---
title: 'Modification avec rupture : Environment. OSVersion retourne la version appropriée du système d’exploitation'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où environnement. OSVersion retourne la version réelle du système d’exploitation au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761308"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion retourne la version appropriée du système d’exploitation

<xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation (OS) au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne une version du système d’exploitation qui peut être incorrecte lorsqu’une application s’exécute en mode de compatibilité Windows. Pour plus d’informations, consultez Remarques sur la [fonction GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).

À compter de .NET 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation.

## <a name="reason-for-change"></a>Motif de modification

Les utilisateurs de cette propriété s’attendent à ce qu’elle retourne la version réelle du système d’exploitation. La plupart des applications .NET ne spécifient pas leur version prise en charge dans leur manifeste d’application, et obtiennent donc la version prise en charge par défaut à partir de l’hôte dotnet. Par conséquent, le shim de compatibilité est rarement significatif pour l’application en cours d’exécution. Lorsque Windows publie une nouvelle version et qu’un ancien hôte dotnet est toujours en cours d’utilisation, ces applications peuvent obtenir une version incorrecte du système d’exploitation. Le retour de la version réelle est plus Inline avec les attentes des développeurs de cette API.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Examinez et testez le code que utilise <xref:System.Environment.OSVersion?displayProperty=nameWithType> pour s’assurer qu’il se comporte comme vous le souhaitez.

## <a name="affected-apis"></a>API affectées

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->

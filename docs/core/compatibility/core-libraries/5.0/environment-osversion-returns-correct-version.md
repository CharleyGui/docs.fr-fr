---
title: 'Modification avec rupture : Environment. OSVersion retourne la version appropriée du système d’exploitation'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où environnement. OSVersion retourne la version réelle du système d’exploitation au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009519"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion retourne la version appropriée du système d’exploitation

<xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation (OS) au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne une version du système d’exploitation qui peut être incorrecte lorsqu’une application s’exécute en mode de compatibilité Windows. Pour plus d’informations, consultez Remarques sur la [fonction GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks). Sur macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version de noyau Darwin sous-jacente.

À compter de .NET 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation pour Windows et MacOS.

Le tableau suivant montre la différence de comportement.

|  | Versions antérieures de .NET | .NET 5 + |
|--|------------------------|---------|
| Windows | 6.2.9200.0 | 10.0.19042.0 |
| macOS | 19.6.0.0 | 10.15.7 |

## <a name="reason-for-change"></a>Motif de modification

Les utilisateurs de cette propriété s’attendent à ce qu’elle retourne la version réelle du système d’exploitation. La plupart des applications .NET ne spécifient pas leur version prise en charge dans leur manifeste d’application, et obtiennent donc la version prise en charge par défaut à partir de l’hôte dotnet. Par conséquent, le shim de compatibilité est rarement significatif pour l’application en cours d’exécution. Lorsque Windows publie une nouvelle version et qu’un ancien hôte dotnet est toujours en cours d’utilisation, ces applications peuvent obtenir une version incorrecte du système d’exploitation. Le retour de la version réelle est plus Inline avec les attentes des développeurs de cette API.

Avec l’introduction de <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> , <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> et <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> dans .net 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> a été modifié pour être cohérent pour Windows et MacOS.

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

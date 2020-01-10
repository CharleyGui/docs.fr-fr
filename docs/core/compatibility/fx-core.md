---
title: Dernières modifications-.NET Framework à .NET Core
description: Répertorie les modifications avec rupture d' .NET Framework à .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: e01ca522b7ec29e2f6db8a5a0c2fcdfc30a38168
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740902"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Dernières modifications pour la migration de .NET Framework vers .NET Core

Si vous migrez une application à partir de .NET Framework vers .NET Core, les modifications avec rupture mentionnées dans cet article peuvent vous affecter. En outre, l’article sur les [technologies .NET Framework non disponibles sur .net Core](../porting/net-framework-tech-unavailable.md) fournit des informations sur les technologies qui ne sont pas prises en charge sur .net Core, par exemple, les domaines d’application et .NET Remoting.

Les modifications avec rupture sont regroupées par catégorie.

> [!NOTE]
> Cet article n’est pas une liste complète des modifications avec rupture entre .NET Framework et .NET Core. Les modifications critiques les plus importantes sont ajoutées ici, car nous en avons conscience.

## <a name="corefx"></a>CoreFx

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a>Windows Forms

Pour plus d’informations sur les modifications avec rupture quand vous migrez une application Windows Forms de .NET Framework vers .NET Core 3,0 ou version ultérieure, consultez [modifications avec rupture dans Windows Forms (.NET Framework à .net Core)](../porting/winforms-breaking-changes.md).

## <a name="see-also"></a>Voir aussi

- [Technologies de .NET Framework indisponibles sur .NET Core](../porting/net-framework-tech-unavailable.md)

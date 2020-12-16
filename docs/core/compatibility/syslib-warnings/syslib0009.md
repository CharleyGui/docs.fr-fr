---
title: AVERTISSEMENT SYSLIB0009
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0009.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 922fcc30b2b1577976e4e88e3f7631e19d4b2cce
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596518"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a>SYSLIB0009 : les méthodes d’authentification et de pré-authentification du AuthenticationManager ne sont pas prises en charge

Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0009` au moment de la compilation.

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a>Supprimer l’avertissement

Si vous ne pouvez pas modifier votre code, vous pouvez supprimer l’avertissement à l’aide d’une `#pragma` directive ou d’un `<NoWarn>` paramètre de projet. Pour obtenir des exemples, consultez [supprimer des avertissements](../syslib-obsoletions.md#suppress-warnings).

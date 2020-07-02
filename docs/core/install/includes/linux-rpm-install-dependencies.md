---
ms.openlocfilehash: 3d8179c5c0e84f8ff1197cce7790c80a5f5a4f6d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619445"
---

Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous. Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :

- krb5-libs
- libicu
- openssl-libs

Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.

Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- [libgdiplus (version 6.0.1 ou ultérieure)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.

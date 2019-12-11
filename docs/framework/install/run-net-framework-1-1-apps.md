---
title: Exécuter des applications .NET Framework 1.1 sur Windows 8, Windows 8.1 ou Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1364eebf4d94a117a3ee7f0912b6ff4090e93853
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960031"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Exécuter des applications .NET Framework 1.1 sur Windows 8, Windows 8.1 ou Windows 10

Le .NET Framework 1,1 n’est pas pris en charge sur les systèmes d’exploitation Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]ou Windows 10. Dans certains cas, .NET Framework 1.1 est spécifiquement identifié conformément aux exigences d’exécution de l’application. Dans ces cas-là, vous devez contacter votre éditeur de logiciels indépendant (ISV) pour mettre à niveau l’application afin qu’elle s’exécute sur .NET Framework 3.5 SP1 ou version ultérieure. Pour plus d’informations, consultez [Migration depuis le .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Installer le .NET Framework 1.1 à partir d’un CD ou du Centre de téléchargement

Il n’est pas possible d’installer manuellement le .NET Framework 1,1 sur Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]ou Windows 10. Elle n'est plus prise en charge. Si vous essayez d'installer le package, le message d'erreur suivant s'affiche : « Le programme d'installation ne peut pas continuer, car cette version du .NET Framework est incompatible avec une version précédemment installée. ». Pour résoudre ce problème, installez le [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Cette version comprend le .NET Framework 2,0 (la version qui suit le .NET Framework 1,1), qui est pris en charge sur Windows 8, Windows 8.1 et Windows 10. Vous devez toujours essayer d’installer l’application en premier pour déterminer si elle est mise à jour automatiquement vers une version ultérieure du .NET Framework. Si ce n’est pas le cas, contactez votre ISV pour une mise à jour de l’application.

## <a name="see-also"></a>Voir aussi

- [Migration à partir du .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Installation du .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](dotnet-35-windows-10.md)

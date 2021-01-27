---
title: Installer le .NET Framework sur Windows 7 SP1
description: Découvrez comment installer le .NET Framework sur Windows 7 SP1.
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899085"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a><span data-ttu-id="08c51-103">Installer le .NET Framework sur Windows 7 SP1 et Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="08c51-103">Install the .NET Framework on Windows 7 SP1 and Windows Server 2008 R2</span></span>

<span data-ttu-id="08c51-104">Un grand nombre d’applications sur Windows nécessitent l’installation du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08c51-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="08c51-105">Pour l’installer, vous pouvez vous aider des instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="08c51-105">You can use the following instructions to install it.</span></span> <span data-ttu-id="08c51-106">Votre présence ici s’explique peut-être par l’affichage sur votre machine de la boîte de dialogue suivante après une tentative d’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="08c51-106">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![Impossible de démarrer cette application](./media/this-application-could-not-be-started.png)

<span data-ttu-id="08c51-108">Ces instructions ont pour but de vous aider à installer les versions du .NET Framework dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="08c51-108">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="08c51-109">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) est la dernière version.</span><span class="sxs-lookup"><span data-stu-id="08c51-109">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest version.</span></span> <span data-ttu-id="08c51-110">Cette version est prise en charge sur Windows 7 SP1 et Windows Server 2008 R2. Elle est fournie avec la [Mise à jour de Windows 10 de mai 2019](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span><span class="sxs-lookup"><span data-stu-id="08c51-110">It is supported on Windows 7 SP1 and Windows Server 2008 R2 and is included with [Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span></span>

## <a name="net-framework-48"></a><span data-ttu-id="08c51-111">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="08c51-111">.NET Framework 4.8</span></span>

> [!div class="button"]
> [<span data-ttu-id="08c51-112">Télécharger .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="08c51-112">Download .NET Framework 4.8</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="08c51-113">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) peut être utilisé pour exécuter des applications conçues pour .NET Framework version 4.0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="08c51-113">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) can be used to run applications built for .NET Framework 4.0 or later.</span></span>

### <a name="offline-installer"></a><span data-ttu-id="08c51-114">programme d’installation hors connexion</span><span class="sxs-lookup"><span data-stu-id="08c51-114">Offline installer</span></span>

<span data-ttu-id="08c51-115">Lorsque vous effectuez une installation hors connexion de .NET Framework sur Windows 7, vous devez d’abord vous assurer que la dernière [autorité de certification racine Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) a été installée sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="08c51-115">When doing an offline install for .NET Framework on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="08c51-116">L’outil _certmgr.exe_ peut automatiser l’installation d’un certificat et est obtenu à partir de Visual Studio ou du SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="08c51-116">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="08c51-117">La commande suivante est utilisée pour installer le certificat avant d’exécuter le programme d’installation de .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="08c51-117">The following command is used to install the certificate before running the .NET Framework installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a><span data-ttu-id="08c51-118">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="08c51-118">.NET Framework 3.5</span></span>

<span data-ttu-id="08c51-119">Le [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) est fourni avec Windows 7.</span><span class="sxs-lookup"><span data-stu-id="08c51-119">The [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) is included with Windows 7.</span></span>

<span data-ttu-id="08c51-120">.NET Framework 3.5 prend en charge les applications conçues pour .NET Framework 1.0 à 3.5.</span><span class="sxs-lookup"><span data-stu-id="08c51-120">The .NET Framework 3.5 supports apps built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="help"></a><span data-ttu-id="08c51-121">Aide</span><span class="sxs-lookup"><span data-stu-id="08c51-121">Help</span></span>

<span data-ttu-id="08c51-122">Vous pouvez [contacter Microsoft pour obtenir de l’aide](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) si vous ne pouvez installer la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08c51-122">You can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) if you cannot get the correct version of the .NET Framework installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="08c51-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08c51-123">See also</span></span>

- [<span data-ttu-id="08c51-124">Télécharger le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08c51-124">Download the .NET Framework</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="08c51-125">Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08c51-125">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="08c51-126">Installer le .NET Framework pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="08c51-126">Install the .NET Framework for developers</span></span>](guide-for-developers.md)

---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603005"
---

<span data-ttu-id="749a8-101">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="749a8-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="749a8-102">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="749a8-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="749a8-103">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="749a8-103">lttng-ust</span></span>
- <span data-ttu-id="749a8-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="749a8-104">libcurl</span></span>
- <span data-ttu-id="749a8-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="749a8-105">openssl-libs</span></span>
- <span data-ttu-id="749a8-106">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="749a8-106">krb5-libs</span></span>
- <span data-ttu-id="749a8-107">libicu</span><span class="sxs-lookup"><span data-stu-id="749a8-107">libicu</span></span>
- <span data-ttu-id="749a8-108">zlib</span><span class="sxs-lookup"><span data-stu-id="749a8-108">zlib</span></span>
- <span data-ttu-id="749a8-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="749a8-109">libunwind</span></span>
- <span data-ttu-id="749a8-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="749a8-110">libuuid</span></span>

<span data-ttu-id="749a8-111">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="749a8-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="749a8-112">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="749a8-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="749a8-113">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="749a8-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="749a8-114">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="749a8-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="749a8-115">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="749a8-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="749a8-116">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="749a8-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

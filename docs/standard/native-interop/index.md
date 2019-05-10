---
title: Interopérabilité native - .NET
description: Découvrez comment interagir avec les composants natifs dans .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b01ea9c17db6da32755309d9c1c2359cecaa1155
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062712"
---
# <a name="native-interoperability"></a><span data-ttu-id="6e5ef-103">Interopérabilité native</span><span class="sxs-lookup"><span data-stu-id="6e5ef-103">Native interoperability</span></span>

<span data-ttu-id="6e5ef-104">Les articles suivants montrent les différentes façons d’utiliser l’« interopérabilité native » dans .NET.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="6e5ef-105">Voici quelques raisons qui peuvent vous inciter à appeler du code natif :</span><span class="sxs-lookup"><span data-stu-id="6e5ef-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="6e5ef-106">Les systèmes d’exploitation sont fournis avec un volume important d’API qui ne sont pas présentes dans les bibliothèques de classes managées.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="6e5ef-107">Un bon exemple pour ce scénario est l’accès à des fonctions de gestion de matériel ou de gestion de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="6e5ef-108">La communication avec d’autres composants qui ont ou peuvent produire des ABI de style C (ABI natifs), comme du code Java qui est exposé via l’[interface JNI (Java Native Interface)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou tout autre langage managé qui peut produire un composant natif.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="6e5ef-109">Sur Windows, la plupart des logiciels qui sont installés, comme la suite Microsoft Office, inscrivent des composants COM qui représentent leurs programmes et permettent aux développeurs de les automatiser ou de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="6e5ef-110">Cela nécessite également l’interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-110">This also requires native interoperability.</span></span>

<span data-ttu-id="6e5ef-111">La liste précédente n’englobe pas toutes les situations et scénarios potentiels dans lesquels le développeur voudrait/aimerait/devrait interagir avec des composants natifs.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="6e5ef-112">La bibliothèque de classes .NET, par exemple, utilise la prise en charge de l’interopérabilité native pour implémenter un certain nombre de ses API, comme la prise en charge et la manipulation de la console, l’accès au système de fichiers, etc.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="6e5ef-113">Toutefois, il est important de noter qu’il existe une option si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="6e5ef-114">La plupart des exemples de cette section sont présentés pour les trois plateformes prises en charge de .NET Core (Windows, Linux et Mac OS).</span><span class="sxs-lookup"><span data-stu-id="6e5ef-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="6e5ef-115">Toutefois, pour certains exemples courts et illustratifs, seuls des noms de fichiers et des extensions Windows sont cités (par exemple, « dll » pour les bibliothèques).</span><span class="sxs-lookup"><span data-stu-id="6e5ef-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="6e5ef-116">Cela ne signifie pas que ces fonctionnalités ne sont pas disponibles sur Linux ou Mac OS, il s’agit d’un choix purement pratique.</span><span class="sxs-lookup"><span data-stu-id="6e5ef-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e5ef-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e5ef-117">See also</span></span>

- [<span data-ttu-id="6e5ef-118">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="6e5ef-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="6e5ef-119">Marshaling de types</span><span class="sxs-lookup"><span data-stu-id="6e5ef-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="6e5ef-120">Meilleures pratiques pour l’interopérabilité native</span><span class="sxs-lookup"><span data-stu-id="6e5ef-120">Native interoperability best practices</span></span>](best-practices.md)

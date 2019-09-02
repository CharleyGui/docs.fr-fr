---
title: 'Atténuation : gestion de versions de produit'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f6016fc43700fda36c6d94408019d25f89bb36b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044208"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="c5e7b-102">Atténuation : gestion de versions de produit</span><span class="sxs-lookup"><span data-stu-id="c5e7b-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="c5e7b-103">Dans .NET Framework 4.6 et ultérieur, la gestion des versions de produit a changé par rapport aux versions précédentes du .NET Framework (.NET Framework 4, 4.5, 4.5.1 et 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="c5e7b-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="c5e7b-104">Modifications de la gestion de versions de produit</span><span class="sxs-lookup"><span data-stu-id="c5e7b-104">Product versioning changes</span></span>

<span data-ttu-id="c5e7b-105">Voici le détail des modifications :</span><span class="sxs-lookup"><span data-stu-id="c5e7b-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="c5e7b-106">La valeur de l’entrée `Version` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` a été remplacée par `4.6.`*xxxxx* pour le .NET Framework 4.6 et ses versions intermédiaires, et par `4.7.`*xxxxx* pour le .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="c5e7b-107">Dans le .NET Framework 4.5, 4.5.1 et 4.5.2, elle était au format `4.5.`*xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="c5e7b-108">La gestion des versions des fichiers et des produits pour les fichiers du .NET Framework est passé de l’ancien schéma `4.0.30319.x` au schéma `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et au schéma `4.7.X.0` pour le .NET Framework 4.7 et ses versions intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="c5e7b-109">Pour voir ces nouvelles valeurs, cliquez avec le bouton droit sur un fichier, puis affichez ses **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="c5e7b-110">Les attributs <xref:System.Reflection.AssemblyFileVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute> pour les assemblys managés ont des valeurs <xref:System.Version> au format `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et `4.7.X.0` pour le Framework .NET 4.7.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="c5e7b-111">À compter de .NET Framework 4.6, la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> retourne la chaîne de version fixe `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="c5e7b-112">Dans .NET Framework 4, 4.5, 4.5.1 et 4.5.2, elle retourne les chaînes de version au format `4.0.30319.xxxxx`, où `xxxxx` est inférieur à 42000 (par exemple « 4.0.30319.18010 »).</span><span class="sxs-lookup"><span data-stu-id="c5e7b-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="c5e7b-113">Notez que nous ne recommandons pas que le code d'application prenne de nouvelles dépendances sur la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="c5e7b-114">Gestion des modifications du contrôle de version de produit</span><span class="sxs-lookup"><span data-stu-id="c5e7b-114">Handling the product versioning changes</span></span>

<span data-ttu-id="c5e7b-115">En général, les applications doivent s'appuyer sur les techniques recommandées pour la détection d'éléments tels que la version de runtime du .NET Framework et le répertoire d'installation :</span><span class="sxs-lookup"><span data-stu-id="c5e7b-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="c5e7b-116">Pour détecter la version du runtime du .NET Framework, consultez [Guide pratique pour déterminer les versions du .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7b-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="c5e7b-117">Pour déterminer le chemin d'installation du .NET Framework, utilisez la valeur de l'entrée `InstallPath` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="c5e7b-118">Le nom de la sous-clé est `NET Framework Setup`, et non `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="c5e7b-119">Pour déterminer le chemin d'accès du répertoire du Common Language Runtime du .NET Framework, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="c5e7b-120">Pour obtenir la version du CLR, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="c5e7b-121">Pour .NET Framework 4 et ses versions intermédiaires (.NET Framework 4.5, 4.5.1, 4.5.2 ainsi que .NET Framework 4.6, 4.6.1, 4.6.2 et 4.7), elle retourne la chaîne `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="c5e7b-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5e7b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5e7b-122">See also</span></span>

- [<span data-ttu-id="c5e7b-123">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="c5e7b-123">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)

---
title: 'Atténuation : Normalisation des chemins d’accès'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181237"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="385d9-102">Atténuation : Normalisation des chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="385d9-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="385d9-103">À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins d’accès dans le .NET Framework a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="385d9-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="385d9-104">Qu’est-ce que la normalisation des chemins d’accès ?</span><span class="sxs-lookup"><span data-stu-id="385d9-104">What is path normalization?</span></span>  
 <span data-ttu-id="385d9-105">La normalisation d’un chemin d’accès implique la modification de la chaîne qui identifie un fichier ou un chemin d’accès afin qu’il soit conforme à un chemin d’accès valide sur le système d’exploitation cible.</span><span class="sxs-lookup"><span data-stu-id="385d9-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="385d9-106">La normalisation implique généralement :</span><span class="sxs-lookup"><span data-stu-id="385d9-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="385d9-107">La mise en forme canonique des composants et séparateurs de répertoires.</span><span class="sxs-lookup"><span data-stu-id="385d9-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="385d9-108">L’application du répertoire actuel à un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="385d9-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="385d9-109">L’évaluation du répertoire relatif (`.`) ou du répertoire parent (`..`) dans un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="385d9-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="385d9-110">La suppression des caractères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="385d9-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="385d9-111">Les changements</span><span class="sxs-lookup"><span data-stu-id="385d9-111">The changes</span></span>  
 <span data-ttu-id="385d9-112">À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins a été modifiée des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="385d9-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="385d9-113">Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) du système d’exploitation pour normaliser les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="385d9-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="385d9-114">La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</span><span class="sxs-lookup"><span data-stu-id="385d9-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="385d9-115">Prise en charge pour la syntaxe de chemin d’accès de périphérique avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers, dans mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="385d9-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="385d9-116">Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.</span><span class="sxs-lookup"><span data-stu-id="385d9-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="385d9-117">L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="385d9-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="385d9-118">Impact</span><span class="sxs-lookup"><span data-stu-id="385d9-118">Impact</span></span>  

<span data-ttu-id="385d9-119">Pour les applications qui ciblent .NET Framework 4.6.2 ou ultérieur, ces modifications sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="385d9-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="385d9-120">Elles améliorent les performances tout en activant des méthodes d’accès à des chemins précédemment inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="385d9-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="385d9-121">Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.</span><span class="sxs-lookup"><span data-stu-id="385d9-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="385d9-122">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="385d9-122">Mitigation</span></span>  
 <span data-ttu-id="385d9-123">Les applications qui ciblent le cadre .NET 4.6.2 ou plus tard peuvent se [ \<](../configure-apps/file-schema/runtime/runtime-element.md) retirer de cette modification et utiliser la normalisation héritée en ajoutant ce qui suit à la section>de temps d’exécution du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="385d9-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="385d9-124">Les applications qui ciblent le cadre .NET 4.6.1 ou plus tôt mais sont en cours d’exécution sur le cadre .NET 4.6.2 ou plus tard peuvent permettre les changements à la normalisation de la trajectoire en ajoutant la ligne suivante à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier .configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="385d9-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="385d9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="385d9-125">See also</span></span>

- [<span data-ttu-id="385d9-126">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="385d9-126">Application compatibility</span></span>](application-compatibility.md)

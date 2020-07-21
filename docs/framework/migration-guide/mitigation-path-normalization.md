---
title: 'Atténuation : Normalisation des chemins d’accès'
description: Découvrez comment la normalisation des chemins d’accès dans .NET Framework a changé à partir des applications qui ciblent .NET Framework 4.6.2.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475214"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="1409c-103">Atténuation : Normalisation des chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="1409c-103">Mitigation: Path Normalization</span></span>
<span data-ttu-id="1409c-104">À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins d’accès dans le .NET Framework a changé.</span><span class="sxs-lookup"><span data-stu-id="1409c-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="1409c-105">Qu’est-ce que la normalisation des chemins d’accès ?</span><span class="sxs-lookup"><span data-stu-id="1409c-105">What is path normalization?</span></span>  
 <span data-ttu-id="1409c-106">La normalisation d’un chemin d’accès implique la modification de la chaîne qui identifie un fichier ou un chemin d’accès afin qu’il soit conforme à un chemin d’accès valide sur le système d’exploitation cible.</span><span class="sxs-lookup"><span data-stu-id="1409c-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="1409c-107">La normalisation implique généralement :</span><span class="sxs-lookup"><span data-stu-id="1409c-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="1409c-108">La mise en forme canonique des composants et séparateurs de répertoires.</span><span class="sxs-lookup"><span data-stu-id="1409c-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="1409c-109">L’application du répertoire actuel à un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="1409c-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="1409c-110">L’évaluation du répertoire relatif (`.`) ou du répertoire parent (`..`) dans un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="1409c-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="1409c-111">La suppression des caractères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1409c-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="1409c-112">Les changements</span><span class="sxs-lookup"><span data-stu-id="1409c-112">The changes</span></span>  
 <span data-ttu-id="1409c-113">À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins a été modifiée des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="1409c-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="1409c-114">Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) du système d’exploitation pour normaliser les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="1409c-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="1409c-115">La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</span><span class="sxs-lookup"><span data-stu-id="1409c-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="1409c-116">Prise en charge pour la syntaxe de chemin d’accès de périphérique avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers, dans mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="1409c-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="1409c-117">Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.</span><span class="sxs-lookup"><span data-stu-id="1409c-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="1409c-118">L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1409c-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="1409c-119">Impact</span><span class="sxs-lookup"><span data-stu-id="1409c-119">Impact</span></span>  

<span data-ttu-id="1409c-120">Pour les applications qui ciblent .NET Framework 4.6.2 ou ultérieur, ces modifications sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="1409c-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="1409c-121">Elles améliorent les performances tout en activant des méthodes d’accès à des chemins précédemment inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="1409c-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="1409c-122">Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.</span><span class="sxs-lookup"><span data-stu-id="1409c-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="1409c-123">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="1409c-123">Mitigation</span></span>  
 <span data-ttu-id="1409c-124">Les applications qui ciblent le .NET Framework 4.6.2 ou version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="1409c-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="1409c-125">Les applications qui ciblent le .NET Framework 4.6.1 ou version antérieure, mais qui s’exécutent sur le .NET Framework 4.6.2 ou version ultérieure, peuvent activer les modifications de la normalisation des chemins d’accès en ajoutant la ligne suivante à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier application. Configuration :</span><span class="sxs-lookup"><span data-stu-id="1409c-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1409c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1409c-126">See also</span></span>

- [<span data-ttu-id="1409c-127">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="1409c-127">Application compatibility</span></span>](application-compatibility.md)

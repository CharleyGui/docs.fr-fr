---
title: 'Atténuation : normalisation des chemins d’accès'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51291fbc9ad2927bc3b9649074a6dbf374aaf7f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648441"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="d01c1-102">Atténuation : normalisation des chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="d01c1-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="d01c1-103">À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la normalisation des chemins d’accès dans .NET Framework a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="d01c1-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="d01c1-104">Qu’est-ce que la normalisation des chemins d’accès ?</span><span class="sxs-lookup"><span data-stu-id="d01c1-104">What is path normalization?</span></span>  
 <span data-ttu-id="d01c1-105">La normalisation d’un chemin d’accès implique la modification de la chaîne qui identifie un fichier ou un chemin d’accès afin qu’il soit conforme à un chemin d’accès valide sur le système d’exploitation cible.</span><span class="sxs-lookup"><span data-stu-id="d01c1-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="d01c1-106">La normalisation implique généralement :</span><span class="sxs-lookup"><span data-stu-id="d01c1-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="d01c1-107">La mise en forme canonique des composants et séparateurs de répertoires.</span><span class="sxs-lookup"><span data-stu-id="d01c1-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="d01c1-108">L’application du répertoire actuel à un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="d01c1-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="d01c1-109">L’évaluation du répertoire relatif (`.`) ou du répertoire parent (`..`) dans un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d01c1-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="d01c1-110">La suppression des caractères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d01c1-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="d01c1-111">Les changements</span><span class="sxs-lookup"><span data-stu-id="d01c1-111">The changes</span></span>  
 <span data-ttu-id="d01c1-112">À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la normalisation des chemins d’accès a changé des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d01c1-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="d01c1-113">Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) du système d’exploitation pour normaliser les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="d01c1-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="d01c1-114">La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</span><span class="sxs-lookup"><span data-stu-id="d01c1-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="d01c1-115">Prise en charge pour la syntaxe de chemin d’accès de périphérique avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers, dans mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="d01c1-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="d01c1-116">Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.</span><span class="sxs-lookup"><span data-stu-id="d01c1-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="d01c1-117">L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="d01c1-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d01c1-118">Impact</span><span class="sxs-lookup"><span data-stu-id="d01c1-118">Impact</span></span>  
 <span data-ttu-id="d01c1-119">Pour les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures, ces modifications sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="d01c1-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="d01c1-120">Elles améliorent les performances tout en activant des méthodes d’accès à des chemins précédemment inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="d01c1-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="d01c1-121">Les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, mais sont en cours d’exécution sous [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou ultérieure ne sont pas affectées par cette modification.</span><span class="sxs-lookup"><span data-stu-id="d01c1-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d01c1-122">Atténuation</span><span class="sxs-lookup"><span data-stu-id="d01c1-122">Mitigation</span></span>  
 <span data-ttu-id="d01c1-123">Les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures peuvent annuler cette modification et utiliser la normalisation héritée en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="d01c1-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="d01c1-124">Les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou versions antérieures mais sont en cours d’exécution sous [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures peuvent activer les modifications apportées à la normalisation des chemins d’accès en ajoutant la ligne suivante à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier .configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="d01c1-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d01c1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d01c1-125">See also</span></span>

- [<span data-ttu-id="d01c1-126">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="d01c1-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

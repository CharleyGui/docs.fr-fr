---
ms.openlocfilehash: 7c4b9faf25853c1c7a546f06c329f6f153eef904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606925"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="f6a24-101">Changements dans la normalisation des chemins</span><span class="sxs-lookup"><span data-stu-id="f6a24-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="f6a24-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f6a24-102">Details</span></span>

<span data-ttu-id="f6a24-103">À partir des applications qui ciblent .NET Framework 4.6.2, la façon dont le runtime normalise les chemins a changé. La normalisation d’un chemin implique la modification de la chaîne qui identifie un chemin ou un fichier afin qu’elle soit conforme à un chemin valide sur le système d’exploitation cible.</span><span class="sxs-lookup"><span data-stu-id="f6a24-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="f6a24-104">La normalisation implique généralement :</span><span class="sxs-lookup"><span data-stu-id="f6a24-104">Normalization typically involves:</span></span>

- <span data-ttu-id="f6a24-105">La mise en forme canonique des composants et séparateurs de répertoires.</span><span class="sxs-lookup"><span data-stu-id="f6a24-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="f6a24-106">L’application du répertoire actuel à un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="f6a24-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="f6a24-107">L’évaluation du répertoire relatif (.) ou du répertoire parent (..) dans un chemin.</span><span class="sxs-lookup"><span data-stu-id="f6a24-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="f6a24-108">La suppression des caractères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f6a24-108">Trimming specified characters.</span></span>
<span data-ttu-id="f6a24-109">À partir des applications qui ciblent .NET Framework 4.6.2, les changements suivants apportés à la normalisation des chemins sont activés par défaut :</span><span class="sxs-lookup"><span data-stu-id="f6a24-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="f6a24-110">Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) du système d’exploitation pour normaliser les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="f6a24-110">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="f6a24-111">La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</span><span class="sxs-lookup"><span data-stu-id="f6a24-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="f6a24-112">Prise en charge de la syntaxe du chemin d’appareil avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers dans mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="f6a24-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="f6a24-113">Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.</span><span class="sxs-lookup"><span data-stu-id="f6a24-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="f6a24-114">L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f6a24-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="f6a24-115">Ces modifications améliorent les performances tout en permettant aux méthodes d’accéder à des chemins auparavant inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="f6a24-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="f6a24-116">Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.</span><span class="sxs-lookup"><span data-stu-id="f6a24-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f6a24-117">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f6a24-117">Suggestion</span></span>

<span data-ttu-id="f6a24-118">Les applications qui ciblent .NET Framework 4.6.2 ou une version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="f6a24-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="f6a24-119">Les applications qui ciblent .NET Framework 4.6.1 ou une version antérieure mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure peuvent activer les changements apportées à la normalisation des chemins en ajoutant la ligne suivante à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="f6a24-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="f6a24-120">Name</span><span class="sxs-lookup"><span data-stu-id="f6a24-120">Name</span></span>    | <span data-ttu-id="f6a24-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="f6a24-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f6a24-122">Étendue</span><span class="sxs-lookup"><span data-stu-id="f6a24-122">Scope</span></span>   | <span data-ttu-id="f6a24-123">Secondaire</span><span class="sxs-lookup"><span data-stu-id="f6a24-123">Minor</span></span>       |
| <span data-ttu-id="f6a24-124">Version</span><span class="sxs-lookup"><span data-stu-id="f6a24-124">Version</span></span> | <span data-ttu-id="f6a24-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f6a24-125">4.6.2</span></span>       |
| <span data-ttu-id="f6a24-126">Type</span><span class="sxs-lookup"><span data-stu-id="f6a24-126">Type</span></span>    | <span data-ttu-id="f6a24-127">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f6a24-127">Retargeting</span></span> |

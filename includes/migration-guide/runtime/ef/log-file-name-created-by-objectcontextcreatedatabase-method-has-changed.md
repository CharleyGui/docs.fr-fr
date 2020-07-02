---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620021"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="9a171-101">Le nom du fichier journal créé par la méthode ObjectContext.CreateDatabase a été changé pour répondre aux spécifications SQL Server</span><span class="sxs-lookup"><span data-stu-id="9a171-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="9a171-102">Détails</span><span class="sxs-lookup"><span data-stu-id="9a171-102">Details</span></span>

<span data-ttu-id="9a171-103">Quand la méthode <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> est appelée directement ou en utilisant Code First avec le fournisseur SqlClient et une valeur AttachDBFilename dans la chaîne de connexion, elle crée un fichier journal nommé nom_fichier_log.ldf au lieu de nom_fichier.ldf (où « nom_fichier » correspond au nom du fichier spécifié par la valeur AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="9a171-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="9a171-104">Cette modification améliore le débogage en fournissant un fichier journal dont le nom répond aux spécifications SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9a171-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9a171-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="9a171-105">Suggestion</span></span>

<span data-ttu-id="9a171-106">Si le nom du fichier journal est important pour une application, celle-ci doit être mise à jour pour attendre le format de nom de fichier standard « _log.ldf ».</span><span class="sxs-lookup"><span data-stu-id="9a171-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="9a171-107">Nom</span><span class="sxs-lookup"><span data-stu-id="9a171-107">Name</span></span>    | <span data-ttu-id="9a171-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="9a171-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a171-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="9a171-109">Scope</span></span>   |<span data-ttu-id="9a171-110">Edge</span><span class="sxs-lookup"><span data-stu-id="9a171-110">Edge</span></span>|
|<span data-ttu-id="9a171-111">Version</span><span class="sxs-lookup"><span data-stu-id="9a171-111">Version</span></span>|<span data-ttu-id="9a171-112">4,5</span><span class="sxs-lookup"><span data-stu-id="9a171-112">4.5</span></span>|
|<span data-ttu-id="9a171-113">Type</span><span class="sxs-lookup"><span data-stu-id="9a171-113">Type</span></span>|<span data-ttu-id="9a171-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="9a171-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a171-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a171-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

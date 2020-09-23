---
title: Impossible de supprimer le journal des événements système
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 444c18f24f63c0c8e206ebf6fe3c77632df2fbd0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078669"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="315ae-102">Impossible de supprimer le journal des événements système</span><span class="sxs-lookup"><span data-stu-id="315ae-102">System event log cannot be deleted</span></span>

<span data-ttu-id="315ae-103">Une tentative de suppression du journal des événements système, qui ne peut pas être supprimé, a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="315ae-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="315ae-104">Le journal système assure le suivi des événements système tels que le démarrage du système et les défaillances de matériel.</span><span class="sxs-lookup"><span data-stu-id="315ae-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="315ae-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="315ae-105">To correct this error</span></span>  
  
- <span data-ttu-id="315ae-106">Songez à configurer votre application de manière à ce qu’elle écrive dans un journal d’application ou un journal personnalisé, plutôt que dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="315ae-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
- <span data-ttu-id="315ae-107">N’essayez pas de supprimer le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="315ae-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315ae-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="315ae-108">See also</span></span>

- <span data-ttu-id="315ae-109">[Administration des journaux des événements](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="315ae-109">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="315ae-110">[Procédure : créer et supprimer des journaux des événements personnalisés](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="315ae-110">[How to: Create and Remove Custom Event Logs](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>

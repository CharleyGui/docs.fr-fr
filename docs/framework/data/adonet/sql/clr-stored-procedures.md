---
title: Procédures stockées du CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: ca0fd2d33f0ad56c96fb63530e6ba3f7f7890f81
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450360"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="3ad13-102">Procédures stockées du CLR</span><span class="sxs-lookup"><span data-stu-id="3ad13-102">CLR Stored Procedures</span></span>
<span data-ttu-id="3ad13-103">Les procédures stockées sont des routines que vous ne pouvez pas utiliser dans des expressions scalaires.</span><span class="sxs-lookup"><span data-stu-id="3ad13-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="3ad13-104">Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="3ad13-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ad13-105">Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="3ad13-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="3ad13-106">Vous devez spécifier pour passer le paramètre par référence et appliquer l’attribut \<out () > pour représenter un paramètre de sortie, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3ad13-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="3ad13-107">Pour plus d’informations, consultez la version de [SQL Server Documentation](/sql) pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3ad13-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="3ad13-108">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3ad13-108">**SQL Server documentation**</span></span>

1. <span data-ttu-id="3ad13-109">[Procédures stockées du CLR](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="3ad13-109">[CLR Stored Procedures](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad13-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad13-110">See also</span></span>

- <span data-ttu-id="3ad13-111">[Création d’objets SQL Server 2005 dans du code managé](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3ad13-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="3ad13-112">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3ad13-112">ADO.NET Overview</span></span>](../ado-net-overview.md)

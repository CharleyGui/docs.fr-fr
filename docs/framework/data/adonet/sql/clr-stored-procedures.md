---
title: Procédures stockées CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d2fde4fdcd5ab63906256d814256578b9baa9ecd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782498"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="34e74-102">Procédures stockées CLR</span><span class="sxs-lookup"><span data-stu-id="34e74-102">CLR Stored Procedures</span></span>
<span data-ttu-id="34e74-103">Les procédures stockées sont des routines pouvant être utilisées dans les expressions scalaires.</span><span class="sxs-lookup"><span data-stu-id="34e74-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="34e74-104">Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="34e74-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34e74-105">Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="34e74-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="34e74-106">Vous devez spécifier pour passer le paramètre par référence et appliquer l' \<attribut out () > pour représenter un paramètre de sortie, comme suit :</span><span class="sxs-lookup"><span data-stu-id="34e74-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="34e74-107">Pour plus d’informations, consultez la version de [SQL Server Documentation](/sql) pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="34e74-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="34e74-108">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="34e74-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="34e74-109">Procédures stockées CLR</span><span class="sxs-lookup"><span data-stu-id="34e74-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="34e74-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34e74-110">See also</span></span>

- <span data-ttu-id="34e74-111">[Création d’objets SQL Server 2005 dans du code managé](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="34e74-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="34e74-112">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="34e74-112">ADO.NET Overview</span></span>](../ado-net-overview.md)

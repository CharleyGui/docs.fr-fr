---
title: Procédures stockées CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: aa14c96ed226ac80a9613d3e229f35dbf5085f3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173612"
---
# <a name="clr-stored-procedures"></a>Procédures stockées CLR

Les procédures stockées sont des routines que vous ne pouvez pas utiliser dans des expressions scalaires. Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.  
  
> [!NOTE]
> Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#. Vous devez spécifier pour passer le paramètre par référence et appliquer l' \<Out()> attribut pour représenter un paramètre de sortie, comme suit :  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Pour plus d’informations, consultez la version de [SQL Server Documentation](/sql) pour la version de SQL Server que vous utilisez.
  
 **Documentation SQL Server**

1. [Procédures stockées du CLR](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>Voir aussi

- [Création d’objets SQL Server 2005 dans du code managé](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)

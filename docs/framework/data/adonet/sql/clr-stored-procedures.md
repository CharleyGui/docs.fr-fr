---
title: Procédures stockées CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c02efa3f0a91d176b626761335bd2d5a2b96b966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917958"
---
# <a name="clr-stored-procedures"></a>Procédures stockées CLR
Les procédures stockées sont des routines pouvant être utilisées dans les expressions scalaires. Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.  
  
> [!NOTE]
> Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#. Vous devez spécifier pour passer le paramètre par référence et appliquer l' \<attribut out () > pour représenter un paramètre de sortie, comme suit:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Pour plus d’informations, consultez la version de [SQL Server Documentation](/sql) pour la version de SQL Server que vous utilisez.
  
 **Documentation SQL Server**

1. [Procédures stockées CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Voir aussi

- [Création d’objets SQL Server 2005 dans du code managé](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)

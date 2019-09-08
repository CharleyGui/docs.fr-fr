---
title: Exemples REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 24830452e6d1ab11605ffa88a925fbc55c80b9bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794709"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="51284-102">Exemples REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="51284-102">REF CURSOR Examples</span></span>
<span data-ttu-id="51284-103">Les exemples de REF CURSOR comprennent les trois exemples Microsoft Visual Basic suivants qui illustrent l'utilisation des REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="51284-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="51284-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="51284-104">Sample</span></span>|<span data-ttu-id="51284-105">Description</span><span class="sxs-lookup"><span data-stu-id="51284-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51284-106">Paramètres REF CURSOR dans un OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="51284-106">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="51284-107">Cet exemple exécute une procédure stockée PL/SQL qui retourne un paramètre REF CURSOR et lit la valeur comme un <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="51284-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="51284-108">Récupération de données à partir de plusieurs REF CURSOR à l’aide d’un OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="51284-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="51284-109">Cet exemple exécute une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et lit les valeurs à l’aide d’un **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="51284-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="51284-110">Remplissage d’un DataSet à l’aide d’un ou de plusieurs REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="51284-110">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="51284-111">Cet exemple exécute une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et remplit un <xref:System.Data.DataSet> avec les lignes qui sont retournées.</span><span class="sxs-lookup"><span data-stu-id="51284-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="51284-112">Pour utiliser ces exemples, il se peut que vous deviez créer les tables Oracle et vous devez créer un package PL/SQL et un corps de package.</span><span class="sxs-lookup"><span data-stu-id="51284-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="51284-113">Création des tables Oracle</span><span class="sxs-lookup"><span data-stu-id="51284-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="51284-114">Ces exemples utilisent des tables définies dans le schéma Oracle Scott/Tiger.</span><span class="sxs-lookup"><span data-stu-id="51284-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="51284-115">Le schéma Oracle Scott/Tiger est fourni avec la plupart des installations Oracle.</span><span class="sxs-lookup"><span data-stu-id="51284-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="51284-116">Si ce schéma n'existe pas, vous pouvez utiliser le fichier de commandes SQL dans {OracleHome}\rdbms\admin\scott.sql pour créer les tables et les index utilisés par ces exemples.</span><span class="sxs-lookup"><span data-stu-id="51284-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="51284-117">Création du package Oracle et du corps de package</span><span class="sxs-lookup"><span data-stu-id="51284-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="51284-118">Ces exemples requièrent le package et le corps de package PL/SQL suivants sur votre serveur</span><span class="sxs-lookup"><span data-stu-id="51284-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="51284-119">Créez le package Oracle suivant sur le serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="51284-119">Create the following Oracle package on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 <span data-ttu-id="51284-120">Créez le corps du package Oracle suivant sur le serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="51284-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="51284-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51284-121">See also</span></span>

- [<span data-ttu-id="51284-122">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="51284-122">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="51284-123">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="51284-123">ADO.NET Overview</span></span>](ado-net-overview.md)

---
title: Manipulation des données dans un DataTable
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 3f98832b4aa9361346d06830f2f004fa374222ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201328"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="ace17-102">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="ace17-102">Manipulating Data in a DataTable</span></span>

<span data-ttu-id="ace17-103">Après avoir créé un objet <xref:System.Data.DataTable> dans un objet <xref:System.Data.DataSet>, vous pouvez réaliser les mêmes opérations que lorsque vous utilisez une table d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="ace17-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="ace17-104">Vous pouvez ajouter, afficher, modifier et supprimer les données de la table, surveiller les erreurs et les événements et interroger les données de la table.</span><span class="sxs-lookup"><span data-stu-id="ace17-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="ace17-105">Lorsque vous modifiez des données dans un **DataTable**, vous pouvez également vérifier si les modifications sont exactes et déterminer si les modifications doivent être acceptées ou rejetées par programmation.</span><span class="sxs-lookup"><span data-stu-id="ace17-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ace17-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ace17-106">In This Section</span></span>  

 [<span data-ttu-id="ace17-107">Ajout de données à un DataTable</span><span class="sxs-lookup"><span data-stu-id="ace17-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="ace17-108">Explique comment créer des lignes et les ajouter à une table.</span><span class="sxs-lookup"><span data-stu-id="ace17-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="ace17-109">Affichage des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="ace17-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="ace17-110">Décrit comment accéder aux données d'une ligne, notamment aux versions actuelles et d'origine des données.</span><span class="sxs-lookup"><span data-stu-id="ace17-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="ace17-111">Méthode Load</span><span class="sxs-lookup"><span data-stu-id="ace17-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="ace17-112">Décrit l’utilisation de la méthode **Load** pour remplir un **DataTable** avec des lignes.</span><span class="sxs-lookup"><span data-stu-id="ace17-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="ace17-113">Modifications de DataTable</span><span class="sxs-lookup"><span data-stu-id="ace17-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="ace17-114">Explique comment modifier les données d'une ligne, notamment suspendre les modifications d'une ligne jusqu'à la vérification et l'acceptation des modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="ace17-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="ace17-115">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="ace17-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="ace17-116">Fournit des informations sur les différents états d'une ligne.</span><span class="sxs-lookup"><span data-stu-id="ace17-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="ace17-117">Suppression de DataRow</span><span class="sxs-lookup"><span data-stu-id="ace17-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="ace17-118">Décrit comment supprimer une ligne d'une table.</span><span class="sxs-lookup"><span data-stu-id="ace17-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="ace17-119">Informations sur l'erreur de ligne</span><span class="sxs-lookup"><span data-stu-id="ace17-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="ace17-120">Explique comment insérer des informations d'erreur par ligne et résoudre les problèmes liés aux données dans une application.</span><span class="sxs-lookup"><span data-stu-id="ace17-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="ace17-121">AcceptChanges et RejectChanges</span><span class="sxs-lookup"><span data-stu-id="ace17-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="ace17-122">Explique comment accepter ou rejeter les modifications apportées à une ligne.</span><span class="sxs-lookup"><span data-stu-id="ace17-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace17-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ace17-123">See also</span></span>

- [<span data-ttu-id="ace17-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="ace17-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="ace17-125">Gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="ace17-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="ace17-126">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ace17-126">ADO.NET Overview</span></span>](../ado-net-overview.md)

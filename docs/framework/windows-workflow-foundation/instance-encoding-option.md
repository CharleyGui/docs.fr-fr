---
title: Option d'encodage d'instance
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279894"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="49f77-102">Option d'encodage d'instance</span><span class="sxs-lookup"><span data-stu-id="49f77-102">Instance Encoding Option</span></span>

<span data-ttu-id="49f77-103">La propriété **option d’encodage d’instance** du magasin d’instances de workflow SQL vous permet de spécifier si le fournisseur de persistance SQL doit compresser les informations d’état de l’instance de workflow à l’aide de l’algorithme gzip avant d’enregistrer les informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="49f77-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="49f77-104">Les valeurs autorisées pour cette propriété sont : Gzip et Aucun.</span><span class="sxs-lookup"><span data-stu-id="49f77-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="49f77-105">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="49f77-105">The default value is None.</span></span> <span data-ttu-id="49f77-106">La liste suivante décrit ces trois options.</span><span class="sxs-lookup"><span data-stu-id="49f77-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="49f77-107">**Gzip**.</span><span class="sxs-lookup"><span data-stu-id="49f77-107">**GZip**.</span></span> <span data-ttu-id="49f77-108">Le fournisseur de persistance encode les informations d'état à l'aide de l'algorithme Gzip avant de rendre les informations d'état persistantes dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="49f77-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="49f77-109">**Aucun**.</span><span class="sxs-lookup"><span data-stu-id="49f77-109">**None**.</span></span> <span data-ttu-id="49f77-110">Le fournisseur de persistance n'encode pas les informations d'état avant d'enregistrer les informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="49f77-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="49f77-111">L'encodage des informations de l'état de l'instance du workflow à l'aide du Gzip réduit la consommation de mémoire dans la base de données SQL ainsi que la consommation réseau si la base de données réside sur un autre ordinateur sur le réseau différent de l'ordinateur sur lequel l'hôte du service de workflow s'exécute.</span><span class="sxs-lookup"><span data-stu-id="49f77-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="49f77-112">Une recommandation générale consiste à définir la propriété de l' **option d’encodage d’instance** sur **None** si l’état de l’instance de workflow est petit.</span><span class="sxs-lookup"><span data-stu-id="49f77-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>

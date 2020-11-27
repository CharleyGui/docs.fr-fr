---
title: Usage of Serialization Binder
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 061afb94d97e3d8a1222e6de9932344fb3ebbe59
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294896"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="74910-102">Usage of Serialization Binder</span><span class="sxs-lookup"><span data-stu-id="74910-102">Usage of Serialization Binder</span></span>

<span data-ttu-id="74910-103">Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.SerializationBinder> pour modifier la version d'un type générique lorsqu'il est sérialisé.</span><span class="sxs-lookup"><span data-stu-id="74910-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="74910-104">Illustre le</span><span class="sxs-lookup"><span data-stu-id="74910-104">Demonstrates</span></span>  

 <span data-ttu-id="74910-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="74910-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="74910-106">Discussions</span><span class="sxs-lookup"><span data-stu-id="74910-106">Discussion</span></span>  

 <span data-ttu-id="74910-107">Cet exemple montre comment deux entités ciblant différentes versions du .NET Framework peuvent communiquer à l’aide du formateur binaire et du Binder de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="74910-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="74910-108">Cet exemple a été développé à l’aide de .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="74910-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="74910-109">Il se compose d’un serveur ciblant .NET Framework 4, qui implémente un contrat avec des types génériques, et deux clients différents, un ciblant .NET Framework 2,0 et un autre ciblant .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="74910-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="74910-110">Le serveur attache un <xref:System.Runtime.Serialization.SerializationBinder> au formateur binary pour être en mesure de modifier la version des types en conséquence lors de la sérialisation, si les deux clients peuvent désérialiser correctement ces types.</span><span class="sxs-lookup"><span data-stu-id="74910-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="74910-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="74910-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="74910-112">Pour exécuter le client, cliquez avec le bouton droit sur la solution, SBGenericsVTS (6 projets), puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="74910-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="74910-113">Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="74910-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="74910-114">Sélectionnez le **serveur** en premier, puis **Client20** , puis **Client40**.</span><span class="sxs-lookup"><span data-stu-id="74910-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="74910-115">Sélectionnez l’action **Démarrer** sur ces trois projets et laissez le reste défini sur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="74910-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="74910-116">Cliquez sur **OK** , puis appuyez sur F5 pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="74910-116">Click **OK** and then press F5 to run the sample.</span></span>

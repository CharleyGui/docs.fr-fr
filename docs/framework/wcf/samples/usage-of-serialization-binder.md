---
title: Usage of Serialization Binder
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348454"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="7e55f-102">Usage of Serialization Binder</span><span class="sxs-lookup"><span data-stu-id="7e55f-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="7e55f-103">Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.SerializationBinder> pour modifier la version d'un type générique lorsqu'il est sérialisé.</span><span class="sxs-lookup"><span data-stu-id="7e55f-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7e55f-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="7e55f-104">Demonstrates</span></span>  
 <span data-ttu-id="7e55f-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="7e55f-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7e55f-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="7e55f-106">Discussion</span></span>  
 <span data-ttu-id="7e55f-107">Cet exemple montre comment deux entités que sont cible différentes versions de peut .NET Framework communiquer à l’aide du formateur binary et le binder de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="7e55f-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="7e55f-108">Cet exemple a été développé à l’aide de .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="7e55f-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="7e55f-109">Il se compose d’un serveur ciblant [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], qui implémente un contrat avec les types génériques et deux clients différents, un ciblage .NET Framework 2.0 et autre ciblant [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e55f-109">It consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="7e55f-110">Le serveur attache un <xref:System.Runtime.Serialization.SerializationBinder> au formateur binary pour être en mesure de modifier la version des types en conséquence lors de la sérialisation, si les deux clients peuvent désérialiser correctement ces types.</span><span class="sxs-lookup"><span data-stu-id="7e55f-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e55f-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7e55f-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="7e55f-112">Pour exécuter le client, cliquez sur la solution, SBGenericsVTS (6 projets), puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7e55f-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="7e55f-113">Dans **propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="7e55f-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="7e55f-114">Sélectionnez **Server** tout d’abord, puis **Client20** , puis **Client40**.</span><span class="sxs-lookup"><span data-stu-id="7e55f-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="7e55f-115">Sélectionnez le **Démarrer** action à ces trois projets et laisser le reste défini sur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="7e55f-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="7e55f-116">Cliquez sur **OK** puis appuyez sur F5 pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="7e55f-116">Click **OK** and then press F5 to run the sample.</span></span>

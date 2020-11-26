---
title: 'Procédure : exporter des métadonnées à partir de points de terminaison de service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: c253358b68cf18a23bab4d12d4ad760874103bff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246405"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="70726-102">Procédure : exporter des métadonnées à partir de points de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="70726-102">How to: Export Metadata from Service Endpoints</span></span>

<span data-ttu-id="70726-103">Cette rubrique explique comment exporter des métadonnées à partir de points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="70726-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="70726-104">Pour exporter des métadonnées à partir de points de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="70726-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="70726-105">Créez un nouveau projet d'application console Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70726-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="70726-106">Ajoutez le code affiché aux étapes suivantes dans le fichier Program.cs généré dans la méthode main().</span><span class="sxs-lookup"><span data-stu-id="70726-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="70726-107">Créez un <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="70726-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="70726-108">Affectez l'une des valeurs de l'énumération <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> à la propriété <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="70726-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="70726-109">Cet exemple affecte <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> à la valeur ce qui correspond à WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="70726-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="70726-110">Créez un tableau d'objets <xref:System.ServiceModel.Description.ServiceEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="70726-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="70726-111">Exportez les métadonnées pour chaque point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="70726-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="70726-112">Vérifiez qu'aucune erreur ne s'est produite pendant le processus d'exportation et récupérez les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="70726-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="70726-113">Vous pouvez maintenant utiliser les métadonnées, par exemple les écrire dans un fichier en appelant la méthode <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29>.</span><span class="sxs-lookup"><span data-stu-id="70726-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70726-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="70726-114">Example</span></span>  

 <span data-ttu-id="70726-115">Les éléments suivants représentent l'intégralité du code pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="70726-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70726-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="70726-116">Compiling the Code</span></span>  

 <span data-ttu-id="70726-117">Lors de la compilation de Program.cs, faites référence à System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="70726-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70726-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70726-118">See also</span></span>

- [<span data-ttu-id="70726-119">Vue d'ensemble de l'architecture de métadonnées</span><span class="sxs-lookup"><span data-stu-id="70726-119">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="70726-120">Utilisation des métadonnées</span><span class="sxs-lookup"><span data-stu-id="70726-120">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="70726-121">Points de terminaison : Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="70726-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)

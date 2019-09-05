---
title: 'Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251379"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="fadcd-102">Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage</span><span class="sxs-lookup"><span data-stu-id="fadcd-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="fadcd-103">Cette rubrique montre comment utiliser l’outil [EDM Generator (EdmGen. exe)](edm-generator-edmgen-exe.md) pour valider les fichiers de modèle et de mappage.</span><span class="sxs-lookup"><span data-stu-id="fadcd-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="fadcd-104">Pour plus d’informations, consultez [Entity Data Model](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="fadcd-104">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="fadcd-105">Pour valider le modèle School à l'aide d'EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="fadcd-105">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="fadcd-106">Créez la base de données School.</span><span class="sxs-lookup"><span data-stu-id="fadcd-106">Create the School database.</span></span> <span data-ttu-id="fadcd-107">Pour plus d’informations, consultez [création de l’exemple de base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fadcd-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="fadcd-108">Générez le modèle School.</span><span class="sxs-lookup"><span data-stu-id="fadcd-108">Generate the School model.</span></span> <span data-ttu-id="fadcd-109">Pour plus d’informations, consultez [Guide pratique pour Utilisez EdmGen. exe pour générer les fichiers](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de modèle et de mappage.</span><span class="sxs-lookup"><span data-stu-id="fadcd-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="fadcd-110">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="fadcd-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fadcd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fadcd-111">See also</span></span>

- <span data-ttu-id="fadcd-112">[Guide pratique : Configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fadcd-112">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="fadcd-113">[Outils de Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fadcd-113">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="fadcd-114">[Guide pratique pour Prégénérer des vues pour améliorer les performances des requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fadcd-114">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="fadcd-115">Guide pratique pour Utiliser EdmGen. exe pour générer le code de couche objet</span><span class="sxs-lookup"><span data-stu-id="fadcd-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

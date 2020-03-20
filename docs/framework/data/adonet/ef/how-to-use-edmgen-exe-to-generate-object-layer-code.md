---
title: 'Comment : utiliser EdmGen.exe pour générer le code de couche objet'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150556"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Comment : utiliser EdmGen.exe pour générer le code de couche objet
Ce sujet montre comment utiliser l’outil [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) pour générer du code de couche d’objet basé sur le fichier .csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet Visual Basic  
  
1. Créez la base de données School. Pour plus d’informations, voir [Créer la base de données sur les échantillons d’écoles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School ou obtenez le fichier School.csdl. Pour plus d’informations, voir [Comment : Utilisez EdmGen.exe pour générer le modèle et cartographier les fichiers](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet C#  
  
1. Créez la base de données School. Pour plus d’informations, voir [Créer la base de données sur les échantillons d’écoles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School ou obtenez le fichier School.csdl. Pour plus d’informations, voir [Comment : Utilisez EdmGen.exe pour générer le modèle et cartographier les fichiers](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Comment : configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Comment : prégénérer les vues pour améliorer les performances des requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et les fichiers de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

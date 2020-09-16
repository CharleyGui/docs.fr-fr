---
title: 'Procédure : Utiliser EdmGen.exe pour générer le code de couche objet'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9a73a803d310ebd847e49f4bd71609f8ef9f2944
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546638"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Procédure : Utiliser EdmGen.exe pour générer le code de couche objet
Cette rubrique montre comment utiliser l’outil [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) pour générer le code de couche objet basé sur le fichier. csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet Visual Basic  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School ou obtenez le fichier School.csdl. Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet C#  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Générez le modèle School ou obtenez le fichier School.csdl. Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Comment : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Comment : prégénérer les vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

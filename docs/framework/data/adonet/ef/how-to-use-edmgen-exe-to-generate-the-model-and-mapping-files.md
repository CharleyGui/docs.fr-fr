---
title: 'Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 8837afd05eec0eaf8ef3e909d46b280e8ae05da7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198182"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage

Cette rubrique montre comment utiliser l'outil EDM Generator (EdmGen.exe) pour générer les fichiers suivants à partir de la base de données School :  
  
- un modèle conceptuel (fichier .csdl) ;  
  
- un modèle de stockage (fichier .ssdl) ;  
  
- un mappage entre les modèles conceptuel et de stockage (fichier .msl) ;  
  
- du code de couche objet en Visual Basic ou C# ;  
  
- des fichiers de vue.  
  
 L'outil EdmGen.exe utilise la commande /mode:FullGeneration pour générer les fichiers répertoriés ci-dessus. Pour plus d’informations sur les commandes EdmGen.exe, consultez [Générateur EDM (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Si vous utilisez EdmGen.exe pour générer les fichiers de modèle et de mappage, vous devez toujours configurer votre projet Visual Studio pour utiliser le Entity Framework. Pour plus d’informations, consultez [procédure : configurer manuellement un projet de Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Un modèle conceptuel généré par EdmGen.exe comprend tous les objets de la base de données. Si vous souhaitez générer un modèle conceptuel qui ne comporte que des objets spécifiques, utilisez l'Assistant EDM. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet Visual Basic  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet C#  
  
1. Créez la base de données School. Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Comment : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Comment : prégénérer les vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

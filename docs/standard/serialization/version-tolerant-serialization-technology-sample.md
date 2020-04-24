---
title: Sérialisation avec tolérance de version, exemple de technologie
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960782"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Sérialisation avec tolérance de version, exemple de technologie
[Télécharger l’exemple](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Cet exemple illustre les fonctionnalités de tolérance de version de la sérialisation .NET. L'exemple génère des applications qui utilisent différentes versions de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour sérialiser et désérialiser des données. En dépit de la présence de versions de type différent, les applications communiquent de façon transparente. Pour plus d’informations, consultez [Sérialisation avec tolérance de version](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Pour générer l'exemple à partir de l'invite de commandes :  
  
1. Ouvrez une fenêtre d'invite de commandes et accédez à l'un des sous-répertoires spécifiques au langage (sous l'application V1 ou l'application V2) pour l'exemple.  
  
2. Tapez **msbuild.exe \<ver> application.sln** sur la ligne de commande (où \<ver> est v1 ou v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio  
  
1. Ouvrez l’Explorateur de fichiers et accédez à l’un des sous-répertoires spécifiques au langage de l’exemple.  
  
2. Accédez au sous-répertoire de l'application V1 du répertoire sélectionné à l'étape précédente.  
  
3. Double-cliquez sur l'icône de V1 Application.sln pour ouvrir le fichier dans Visual Studio.  
  
4. Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
5. Accédez au sous-répertoire de l'application V2 et répétez les deux étapes précédentes pour générer l'application V2.  
  
 Les applications seront générées dans le sous-répertoire \bin ou \bin\Debug par défaut de leur projet respectif.  
  
### <a name="to-run-the-sample"></a>Exécution de l'exemple  
  
1. Dans la fenêtre d'invite de commandes, accédez au sous-répertoire spécifique au langage que vous avez sélectionné lors de la création des exemples d'applications.  
  
2. Tapez **runme.cmd** sur la ligne de commande pour exécuter en même temps les deux applications.  
  
 Vous pouvez aussi accéder aux répertoires qui contiennent les nouveaux fichiers exécutables et les exécuter séquentiellement.  
  
> [!NOTE]
> L'exemple génère des applications console. Vous devez les lancer et les exécuter dans une fenêtre d'invite de commandes pour consulter leur sortie.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>

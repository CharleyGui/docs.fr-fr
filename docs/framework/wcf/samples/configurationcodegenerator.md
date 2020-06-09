---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592474"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
Le ConfigurationCodeGenerator est un outil que vous pouvez utiliser pour exposer vos implémentations de canal personnalisées au système de configuration. Cela permet aux utilisateurs de votre canal personnalisé de configurer votre canal en utilisant un fichier .config comme ils configureraient une liaison fournie par le système telle que `NetTcpBinding` ou une liaison personnalisée à l'aide de `TcpTransportBindingElement`.  
  
 Lorsque vous écrivez un canal personnalisé et l'exposez au modèle de programmation en utilisant un nouveau `BindingElement` ou une `Binding`, vous devez créer un ensemble de classes pour rendre le `BindingElement` ou la `Binding` configurable à l'aide d'un fichier .config. Vous pouvez utiliser l'outil ConfigurationCodeGenerator pour générer ces classes et améliorer l'expérience de votre client.  
  
### <a name="to-build-the-tool"></a>Pour générer l'outil  
  
1. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
2. La génération de la solution génère un fichier : ConfigurationCodeGenerator.exe. Le fichier SampleRun. cmd contient un exemple de ligne de commande qui montre comment utiliser cet outil pour générer les classes de l’exemple [transport : UDP](transport-udp.md) .  
  
### <a name="to-run-the-tool"></a>Pour exécuter l'outil  
  
1. Dans l'invite de commandes, tapez ce qui suit si vous avez à la fois un type `BindingElement` personnalisé et un type `Binding` personnalisé :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Ou tapez ce qui suit si vous avez uniquement un type `BindingElement` personnalisé :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Ou tapez ce qui suit si vous avez uniquement un type `Binding` personnalisé :  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     La commande génère trois fichiers .cs pour le `BindingElement` (si vous avez spécifié l'option /be:), cinq fichiers .cs pour la `Binding` standard (si vous avez spécifié l'option /sb:), et un fichier .xml.  
  
    1. Si vous avez utilisé l’option /be, l’un des fichiers .cs implémente `BindingElementExtensionSection` pour votre élément de liaison. Ce code expose votre `BindingElement` au système de configuration, afin que d'autres liaisons personnalisées puissent utiliser votre élément de liaison. Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes. Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.  
  
    2. Si vous avez spécifié l'option /sb, deux des fichiers .cs implémentent respectivement un `StandardBindingElement` et un `StandardBindingCollectionElement`, qui expose votre liaison standard au système de configuration. Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes. Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.  
  
         Si vous avez spécifié l’option l'/SB :, CodeToAddTo \<*YourStdBinding*> . cs contient du code que vous devez ajouter manuellement dans la classe qui implémente votre liaison standard.  
  
     Le fichier SampleConfig.xml contient le code de configuration que vous devez ajouter au fichier de configuration qui enregistre les gestionnaires définis à l'étape 1 ou 2 précédente.  

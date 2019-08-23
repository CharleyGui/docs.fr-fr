---
title: Reconnaissance d'écriture manuscrite
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956529"
---
# <a name="handwriting-recognition"></a>Reconnaissance d'écriture manuscrite
Cette section présente les notions de base de la reconnaissance relative à l’encre numérique dans la plateforme WPF.  
  
## <a name="recognition-solutions"></a>Solutions de reconnaissance  
 L’exemple suivant montre comment reconnaître de l’encre à l’aide de la classe [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)).  
  
> [!NOTE]
> Cet exemple nécessite que les modules de reconnaissance d’écriture manuscrite soient installés sur le système.  
  
 Créez un projet d’application WPF dans Visual Studio, intitulé **InkRecognition**. Remplacez le contenu du fichier Window1.xaml par le code XAML suivant. Ce code restitue l’interface utilisateur de l’application.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Ajoutez une référence à l’assembly Microsoft Annotations, Microsoft.Ink.dll, qui se trouve dans \Program Files\Common Files\Microsoft Shared\Ink. Remplacez le contenu du fichier code-behind par le code suivant.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))

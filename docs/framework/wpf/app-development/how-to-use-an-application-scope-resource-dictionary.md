---
title: Guide pratique pour utiliser un dictionnaire de ressources de portée application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459800"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Guide pratique pour utiliser un dictionnaire de ressources de portée application
Cet exemple montre comment définir et utiliser un dictionnaire de ressources personnalisé de portée application.  
  
## <a name="example"></a>Exemple  
 <xref:System.Windows.Application> expose un magasin de portée application pour les ressources partagées : <xref:System.Windows.Application.Resources%2A>. Par défaut, la propriété <xref:System.Windows.Application.Resources%2A> est initialisée avec une instance du type <xref:System.Windows.ResourceDictionary>. Vous utilisez cette instance lorsque vous récupérez et définissez des propriétés de portée application à l’aide de <xref:System.Windows.Application.Resources%2A>. Pour plus d’informations, consultez Guide pratique [pour obtenir et définir une ressource de portée application](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Si vous avez plusieurs ressources que vous définissez à l’aide de <xref:System.Windows.Application.Resources%2A>, vous pouvez utiliser à la place un dictionnaire de ressources personnalisé pour stocker ces ressources et y définir <xref:System.Windows.Application.Resources%2A>. L’exemple suivant montre comment déclarer un dictionnaire de ressources personnalisé à l’aide de XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 L’échange de dictionnaires de ressources entiers à l’aide de <xref:System.Windows.Application.Resources%2A> vous permet de prendre en charge des thèmes de portée application, où chaque thème est encapsulé par un dictionnaire de ressources unique. L'exemple suivant montre comment définir <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 L’exemple suivant montre comment vous pouvez récupérer des ressources de portée application à partir du dictionnaire de ressources exposé par <xref:System.Windows.Application.Resources%2A> en XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Voici également comment obtenir les ressources dans le code.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Il y a deux considérations à prendre en compte lors de l’utilisation de <xref:System.Windows.Application.Resources%2A>. Premièrement, la *clé* de dictionnaire est un objet. vous devez donc utiliser exactement la même instance d’objet lorsque vous définissez et obtenez une valeur de propriété. (Notez que la clé respecte la casse lors de l’utilisation d’une chaîne.) Deuxièmement, la *valeur* de dictionnaire est un objet. vous devez donc convertir la valeur en type souhaité lors de l’obtention d’une valeur de propriété.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Dictionnaires de ressources fusionnés](../advanced/merged-resource-dictionaries.md)

---
title: 'Comment: Convertir entre .NET Framework et Windows Runtime streams (Windows uniquement)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159466"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Comment: Convertir entre .NET Framework et Windows Runtime streams (Windows uniquement)

Le .NET Framework pour les applications UWP est un sous-ensemble du .NET Framework complet. En raison de la sécurité et d’autres spécifications des applications UWP, vous ne pouvez pas utiliser l’ensemble d’API .NET Framework pour ouvrir et lire des fichiers. Pour plus d’informations, consultez [Vue d’ensemble de .NET pour les applications UWP](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Toutefois, vous pouvez utiliser des API .NET Framework pour les autres opérations de manipulation des flux. Pour manipuler ces flux, vous pouvez convertir un flux .NET Framework, tel que <xref:System.IO.MemoryStream> ou <xref:System.IO.FileStream>, en flux Windows Runtime tel que <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream> ou <xref:Windows.Storage.Streams.IRandomAccessStream>.

La classe <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> contient des méthodes qui rendent ces conversions plus faciles. Toutefois, il existe des différences sous-jacentes entre les flux .NET Framework et Windows Runtime qui affecteront les résultats obtenus lors de l’utilisation de ces méthodes, comme l’expliquent les sections suivantes :

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Convertir un flux Windows Runtime en flux .NET Framework
Pour convertir un flux Windows Runtime en un flux .NET Framework, utilisez l’une des méthodes <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> suivantes :

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> convertit un flux d’accès aléatoire Windows Runtime en un flux managé dans .NET pour les applications de plateforme Windows universelle (UWP).
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType> convertit un flux de sortie dans Windows Runtime en un flux managé dans .NET pour les applications de plateforme Windows universelle (UWP).
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> convertit un flux d’entrée dans Windows Runtime en un flux managé dans .NET pour les applications de plateforme Windows universelle (UWP).

Windows Runtime propose des types de flux qui prennent en charge la lecture seule, l’écriture seule et la lecture-écriture. Ces fonctionnalités sont conservées lorsque vous convertissez un flux Windows Runtime en flux .NET Framework. En outre, si vous convertissez un flux Windows Runtime en un flux .NET Framework et inversement, vous obtenez l'instance du Windows Runtime en retour.

Il est recommandé d’utiliser la méthode de conversion qui correspond aux fonctionnalités du flux Windows Runtime que vous souhaitez convertir. Toutefois, comme <xref:Windows.Storage.Streams.IRandomAccessStream> est accessible en lecture et en écriture (il implémente <xref:Windows.Storage.Streams.IOutputStream> et <xref:Windows.Storage.Streams.IInputStream>), les méthodes de conversion conservent les fonctionnalités du flux d’origine. Par exemple, l’utilisation de <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> pour convertir <xref:Windows.Storage.Streams.IRandomAccessStream> n’empêche pas le flux .NET Framework converti d’être accessible en lecture. Il est également accessible en écriture.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Exemple : Convertir Windows Runtime accès aléatoire au flux cadre .NET
Pour convertir un flux d’accès aléatoire Windows Runtime en un flux .NET Framework, utilisez la méthode <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>.

L’exemple de code suivant vous invite à sélectionner un fichier, l’ouvre à l’aide des API Windows Runtime, puis le convertit en flux .NET Framework. Il lit le flux et l’exporte vers un bloc de texte. En général, vous devez manipuler le flux à l’aide des API .NET Framework avant de sortir les résultats.

Pour exécuter cet exemple, créez une application XAML UWP, contenant un bloc de texte nommé `TextBlock1` et un bouton nommé `Button1`. Associez l’événement de clic de bouton à la méthode `button1_Click` qui est illustrée dans l’exemple.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Convertir un flux .NET Framework en flux Windows Runtime
Pour convertir un flux .NET Framework en un flux Windows Runtime, utilisez l’une des méthodes <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> suivantes :

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> convertit un flux managé dans .NET pour les applications de plateforme Windows universelle (UWP) en un flux d’entrée dans Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> convertit un flux managé dans .NET pour les applications de plateforme Windows universelle (UWP) en un flux de sortie dans Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType> convertit un flux managé dans .NET pour les applications UWP en un flux d’accès aléatoire que Windows Runtime peut utiliser pour la lecture ou l’écriture.

Lorsque vous convertissez un flux .NET Framework en flux Windows Runtime, les fonctionnalités du flux converti dépendent de celles du flux d’origine. Par exemple, si le flux d’origine prend en charge la lecture et l’écriture, et que vous appelez <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> pour convertir le flux, le type retourné est un `IRandomAccessStream`. `IRandomAccessStream` implémente `IInputStream` et `IOutputStream`, et prend en charge la lecture et l’écriture.

Les flux .NET Framework ne prennent pas en charge le clonage, même après la conversion. Si vous convertissez un flux .NET Framework en flux Windows Runtime, et appelez <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> ou <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, qui appelle <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, ou si vous appelez <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> directement, une exception est levée.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Exemple : Convertir le cadre .NET en flux d’accès aléatoire Windows Runtime

Pour convertir un flux .NET Framework en flux d’accès aléatoire Windows Runtime, utilisez une méthode <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A>, comme indiqué dans l’exemple suivant :

> [!IMPORTANT]
> Vérifiez que le flux du .NET Framework que vous utilisez prend en charge la recherche, ou copiez-le dans un flux qui la prend en charge. Vous pouvez utiliser la propriété <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> pour le déterminer.

Pour exécuter cet exemple, créez une application XAML UWP qui cible .NET Framework 4.5.1 et contient un bloc de texte nommé `TextBlock2` et un bouton nommé `Button2`. Associez l’événement de clic de bouton à la méthode `button2_Click` qui est illustrée dans l’exemple.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Voir aussi

- [Quickstart: Lire et écrire un fichier (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Vue d’ensemble de .NET pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [.NET pour les API d’applications du Windows Store](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  

---
title: Références faibles
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2e2fd6f46a430424e6010adbe0662b5bd3db7ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622658"
---
# <a name="weak-references"></a>Références faibles
Le Garbage collector ne peut pas collecter un objet actuellement utilisé par une application, tandis que le code de l’application peut accéder à cet objet. On dit de l’application qu’elle a une référence forte à l’objet.  
  
 Une référence faible permet au Garbage collector de collecter l’objet tout en permettant à l’application d’y accéder. Une référence faible est valide uniquement pour une période indéterminée jusqu’à ce que l’objet soit collecté quand il n’existe aucune référence forte. Quand vous utilisez une référence faible, l’application peut toujours obtenir une référence forte à l’objet, ce qui l’empêche d’être collecté. Toutefois, il existe toujours un risque que le Garbage collector accède à l’objet avant qu’une référence forte soit rétablie.  
  
 Les références faibles sont utiles pour les objets qui utilisent beaucoup de mémoire, mais peuvent être recréées facilement si elles sont récupérées par le garbage collection.  
  
 Supposons que l’arborescence d’une application Windows Forms présente à l’utilisateur un choix hiérarchique d’options complexe. Si les données sous-jacentes sont volumineuses, la conservation de l’arborescence en mémoire est inefficace quand l’utilisateur est impliqué dans un autre élément de l’application.  
  
 Quand l’utilisateur passe à une autre partie de l’application, vous pouvez utiliser la classe <xref:System.WeakReference> pour créer une référence faible à l’arborescence et détruire toutes les références fortes. Quand l’utilisateur revient à l’arborescence, l’application tente d’obtenir une référence forte à l’arborescence et, en cas de réussite, évite de reconstruire l’arborescence.  
  
 Pour établir une référence faible à un objet, vous créez un <xref:System.WeakReference> à l’aide de l’instance de l’objet à suivre. Vous affectez ensuite cet objet à la propriété <xref:System.WeakReference.Target%2A> et vous définissez la référence d’origine à l’objet sur `null`. Pour obtenir un exemple de code, consultez <xref:System.WeakReference> dans la bibliothèque de classes.  
  
## <a name="short-and-long-weak-references"></a>Références faibles courtes et longues  
 Vous pouvez créer une référence faible courte ou une référence faible longue :  
  
- Courte  
  
     La cible d’une référence faible courte devient `null` quand l’objet est récupéré par le garbage collection. La référence faible est elle-même un objet managé et fait l’objet d’un garbage collection comme tout autre objet managé.  Une référence faible courte est le constructeur par défaut <xref:System.WeakReference>.  
  
- Longue  
  
     Une référence faible longue est conservée après l’appel de la méthode <xref:System.Object.Finalize%2A>. Cela permet à l’objet d’être recréé, mais l’état de l’objet reste imprévisible. Pour utiliser une référence longue, spécifiez `true` dans le constructeur <xref:System.WeakReference>.  
  
     Si le type de l’objet ne dispose pas d’une méthode <xref:System.Object.Finalize%2A>, la fonctionnalité de la référence faible courte s’applique et la référence faible est valide uniquement jusqu’à la collecte de la cible, ce qui peut se produire à tout moment après l’exécution du finaliseur.  
  
 Pour établir une référence forte et réutiliser l’objet, effectuez un cast de la propriété <xref:System.WeakReference.Target%2A> d’un <xref:System.WeakReference> vers le type de l’objet. Si la propriété <xref:System.WeakReference.Target%2A> retourne la valeur `null`, l’objet a été collecté ; sinon, vous pouvez continuer à utiliser l’objet, car l’application a récupéré une référence forte à celui-ci.  
  
## <a name="guidelines-for-using-weak-references"></a>Instructions d’utilisation de références faibles  
 Utilisez des références faibles longues uniquement quand cela est nécessaire, car l’état de l’objet est imprévisible après la finalisation.  
  
 Évitez d’utiliser des références faibles aux petits objets, car le pointeur lui-même peut être de la même taille ou d’une taille supérieure.  
  
 Évitez d’utiliser les références faibles comme solution automatique aux problèmes de gestion de la mémoire. Développez plutôt une stratégie de mise en cache efficace pour gérer les objets de votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)

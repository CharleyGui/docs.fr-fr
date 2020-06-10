---
title: Fichiers mappés en mémoire
description: Explorez les fichiers mappés en mémoire dans .NET, qui contiennent le contenu du fichier dans la mémoire virtuelle, et autorisez les applications à modifier le fichier en écrivant directement dans la mémoire.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: db63c15357b0670c55b1174b91b02e2f49a0c4c1
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661977"
---
# <a name="memory-mapped-files"></a>Fichiers mappés en mémoire
Un fichier mappé en mémoire comporte le contenu d'un fichier en mémoire virtuelle. Ce mappage entre un fichier et un espace mémoire permet à une application incluant plusieurs processus de modifier le fichier en lisant et en écrivant directement dans la mémoire. À compter de .NET Framework 4, vous pouvez utiliser du code managé pour accéder aux fichiers mappés en mémoire de la même façon que les fonctions Windows natives accèdent à des fichiers mappés en mémoire, comme décrit dans [Gestion des fichiers mappés en mémoire](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Il existe deux types de fichiers mappés en mémoire :  
  
- Fichiers mappés en mémoire persistants  
  
     Les fichiers persistants sont des fichiers mappés en mémoire associés à un fichier source sur un disque. Lorsque le dernier processus a fini de travailler avec le fichier, les données sont enregistrées dans le fichier source sur le disque. Ces fichiers mappés en mémoire sont adaptés au travail avec des fichiers sources extrêmement volumineux.  
  
- Fichiers mappés en mémoire non persistants  
  
     Les non fichiers persistants sont des fichiers mappés en mémoire associés à un fichier sur un disque. Lorsque le dernier processus a fini de travailler avec le fichier, les données sont perdues et l'espace mémoire est récupéré par le nettoyage de la mémoire. Ces fichiers sont adaptés à la création d’une mémoire partagée pour les communications entre processus (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Processus, vues et gestion de la mémoire  
 Les fichiers mappés en mémoire ne peuvent pas être partagé entre plusieurs processus. Des processus peuvent être mappés dans le même fichier mappé en mémoire à l’aide d’un nom commun attribué par le processus qui a créé le fichier.  
  
 Pour utiliser un fichier mappé en mémoire, vous devez créer une vue de l’intégralité du fichier mappé en mémoire ou une partie de celui-ci. Vous pouvez également créer plusieurs vues dans la même partie du fichier mappé en mémoire et créer ainsi une mémoire simultanée. Pour que deux vues restent simultanées, elles doivent être créées à partir du même fichier mappé en mémoire.  
  
 Plusieurs vues peuvent également être nécessaires si le fichier est supérieur à la taille de l’espace de mémoire logique de l’application disponible pour le mappage de mémoire (2 Go sur un ordinateur 32 bits).  
  
 Il existe deux types de vues : une vue d’accès à Stream et une vue d’accès aléatoire. Utilisez les vues d’accès à Stream pour un accès séquentiel à un fichier ; c’est recommandé pour les fichiers non persistants et pour IPC. Les vues d’accès aléatoire sont privilégiées pour l’utilisation de fichiers persistants.  
  
 Les fichiers mappés en mémoire sont accessibles via le gestionnaire de mémoire du système d’exploitation. Le fichier est alors automatiquement partitionné en un nombre de pages et consulté en fonction des besoins. Vous n’avez pas à gérer vous-même la mémoire.  
  
 L’illustration suivante montre comment plusieurs processus peuvent avoir simultanément plusieurs vues qui se chevauchent dans le même fichier mappé en mémoire.

 L’image suivante montre plusieurs vues qui se chevauchent dans un fichier mappé en mémoire :  
  
 ![Capture d’écran qui montre des vues dans un fichier mappé en mémoire.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programmation avec des fichiers mappés en mémoire  
 Le tableau suivant fournit un guide pour l’utilisation d’objets de fichier mappé en mémoire et de leurs membres.  
  
|Tâche|Méthodes ou propriétés à utiliser|  
|----------|----------------------------------|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire persistant à partir d’un fichier sur disque.|Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> .|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire non persistant (pas associé à un fichier sur disque).|Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> .<br /><br /> - ou -<br /><br /> Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> .|  
|Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> d’un fichier mappé en mémoire existant (persistant ou non persistant).|Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> .|  
|Pour obtenir un objet <xref:System.IO.UnmanagedMemoryStream> pour une vue à accès séquentiel dans le fichier mappé en mémoire.|Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> .|  
|Pour obtenir un objet <xref:System.IO.UnmanagedMemoryAccessor> pour une vue à accès aléatoire dans un fichier mappé en mémoire.|Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> .|  
|Pour obtenir un objet <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> à utiliser avec du code non managé.|Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.|  
|Pour différer l’allocation de mémoire jusqu’à ce qu’une vue soit créée (fichiers non persistants uniquement).<br /><br /> (Pour déterminer la taille de page du système actuel, utilisez la propriété <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.)|Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> avec la valeur <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> qui ont une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> en tant que paramètre.|  
  
### <a name="security"></a>Sécurité  
 Vous pouvez appliquer des droits d’accès lorsque vous créez un fichier mappé en mémoire, en utilisant les méthodes suivantes qui prennent une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> en tant que paramètre :  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 vous pouvez spécifier des droits d’accès pour l’ouverture d’un fichier mappé en mémoire existant à l’aide des méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> en tant que paramètre.  
  
 Vous pouvez également inclure un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> qui contient des règles d’accès prédéfinies.  
  
 Pour appliquer des règles d’accès nouvelles ou modifiées à un fichier mappé en mémoire, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>. Pour récupérer un accès ou des règles d’audit à partir d’un fichier existant, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.  
  
## <a name="examples"></a>Exemples  
  
### <a name="persisted-memory-mapped-files"></a>Fichiers mappés en mémoire persistants  
 Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> créent un fichier mappé en mémoire à partir d’un fichier existant sur le disque.  
  
 L’exemple suivant crée une vue mappée en mémoire d’une partie d’un fichier très volumineux et manipule une partie de ce dernier.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 L’exemple suivant ouvre le même fichier mappé en mémoire pour un autre processus.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Fichiers mappés en mémoire non persistants  
 Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> et <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> créent un fichier mappé en mémoire qui n’est pas mappé à un fichier existant sur le disque.  
  
 L’exemple suivant se compose de trois processus distincts (applications console) qui écrivent des valeurs booléennes dans un fichier mappé en mémoire. La séquence d’actions suivante se produit :  
  
1. `Process A` crée le fichier mappé en mémoire et y écrit une valeur.  
  
2. `Process B` ouvre le fichier mappé en mémoire et y écrit une valeur.  
  
3. `Process C` ouvre le fichier mappé en mémoire et y écrit une valeur.  
  
4. `Process A` lit et affiche les valeurs à partir du fichier mappé en mémoire.  
  
5. Après que `Process A` est terminé avec le fichier mappé en mémoire, ce dernier est immédiatement récupéré par le nettoyage de la mémoire.  
  
 Pour exécuter cet exemple, procédez comme suit :  
  
1. Compilez les applications et ouvrez trois fenêtres d’invite de commandes.  
  
2. Dans la première fenêtre d’invite de commande, exécutez `Process A`.  
  
3. Dans la deuxième fenêtre d’invite de commande, exécutez `Process B`.  
  
4. Retournez à `Process A` et appuyez sur ENTRÉE.  
  
5. Dans la troisième fenêtre d’invite de commande, exécutez `Process C`.  
  
6. Retournez à `Process A` et appuyez sur ENTRÉE.  
  
 La sortie de `Process A` est la suivante :  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Processus A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Processus B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Processus C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [E/s de fichier et de flux](index.md)

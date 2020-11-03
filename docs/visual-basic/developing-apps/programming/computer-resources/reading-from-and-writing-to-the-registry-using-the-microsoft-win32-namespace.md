---
title: Lecture et écriture dans le Registre à l'aide de l'espace de noms Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 58c3a92067cd0be5db02231c5fc1a13b429a60a0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282233"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Lecture et écriture dans le Registre à l'aide de l'espace de noms Microsoft.Win32 (Visual Basic)

Bien que `My.Computer.Registry` doit couvrir vos besoins de base lors de la programmation par rapport au registre, vous pouvez également utiliser les <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> classes et dans l' <xref:Microsoft.Win32> espace de noms de .net.
  
## <a name="keys-in-the-registry-class"></a>Clés dans la classe de Registre  

 La classe <xref:Microsoft.Win32.Registry> fournit les clés de Registre de base qui peuvent être utilisées pour accéder aux sous-clés et à leurs valeurs. Les clés de base proprement dites sont en lecture seule. Le tableau suivant répertorie et décrit les sept clés exposées par la classe <xref:Microsoft.Win32.Registry>.  
  
|**Clé**|**Description**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Définit les types de documents et les propriétés associées à ces types.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Contient des informations sur la configuration matérielle qui ne sont pas propres à l’utilisateur.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Contient des informations sur les préférences de l’utilisateur actuel, telles que les variables d’environnement.|  
|<xref:Microsoft.Win32.Registry.DynData>|Contient des données de Registre dynamiques, telles que celles utilisées par les pilotes de périphériques virtuels.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Contient cinq sous-clés (Hardware, SAM, Security, Software et System) qui contiennent les données de configuration de l’ordinateur local.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Contient des informations sur les performances des composants logiciels.|  
|<xref:Microsoft.Win32.Registry.Users>|Contient des informations sur les préférences de l’utilisateur par défaut.|  
  
> [!IMPORTANT]
> Il est plus sûr d’écrire des données dans l’utilisateur actuel (<xref:Microsoft.Win32.Registry.CurrentUser>) que dans l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>). Une condition généralement appelée « usurpation » se produit quand la clé que vous créez a été créée précédemment par un autre processus, potentiellement malveillant. Pour éviter ce problème, utilisez une méthode, telle que <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, qui retourne `Nothing` si la clé n’existe pas encore.  
  
## <a name="reading-a-value-from-the-registry"></a>Lecture d’une valeur à partir du Registre  

 Le code suivant montre comment lire une chaîne à partir de HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Le code suivant lit, incrémente puis écrit une chaîne dans HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally (instruction)](../../../language-reference/statements/try-catch-finally-statement.md)
- [Lecture et écriture dans le Registre](reading-from-and-writing-to-the-registry.md)
- [Sécurité et Registre](security-and-the-registry.md)

---
title: 'Procédure : créer une clé de Registre et définir sa valeur'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: b51a14e5e9c69078330f5b2161f74cff8e4da332
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363446"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Guide pratique pour créer une clé de Registre et définir sa valeur en Visual Basic

Vous pouvez utiliser la méthode `CreateSubKey` de l’objet `My.Computer.Registry` pour créer une clé de Registre.

## <a name="procedure"></a>Procédure

### <a name="to-create-a-registry-key"></a>Pour créer une clé de Registre

- Utilisez la méthode `CreateSubKey`, en spécifiant le nom de la clé et sous quelle ruche la placer. Le paramètre `Subkey` ne respecte pas la casse. Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Pour créer une clé de Registre et définir sa valeur

1. Utilisez la méthode `CreateSubkey`, en spécifiant le nom de la clé et sous quelle ruche la placer. Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Définissez la valeur avec la méthode `SetValue`. Cet exemple définit « This is a test value » comme valeur de chaîne « MyTestKeyValue ».

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Exemple

Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER, puis affecte `This is a test value` comme valeur de chaîne `MyTestKeyValue`.

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Programmation fiable

Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé. Par exemple, vous souhaiterez peut-être ouvrir la clé HKEY_CURRENT_USER\Software de l’utilisateur actuel et créer une clé avec le nom de votre société. Ensuite, ajoutez les valeurs de Registre à la clé de votre société.

Lors de la lecture du Registre à partir d’une application web, l’utilisateur actuel dépend de l’authentification et de l’emprunt d’identité implémenté dans l’application web.

Il est plus sûr d’écrire des données dans le dossier utilisateur (<xref:Microsoft.Win32.Registry.CurrentUser>) que sur l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>).

Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà. Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès. Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus. Pour l’éviter, utilisez la méthode <xref:Microsoft.Win32.RegistryKey.GetValue%2A>. Elle retourne `Nothing` si la clé n’existe pas encore.

Il est dangereux de stocker des données confidentielles (telles que des mots de passe) dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.

Les conditions ci-dessous peuvent générer une exception.

- Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).

- L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre (<xref:System.Security.SecurityException>).

- Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).

- La clé est fermée (<xref:System.IO.IOException>).

- La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).

## <a name="net-framework-security"></a>Sécurité du .NET Framework

Pour exécuter ce processus, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. De même, l’utilisateur doit disposer de listes de contrôle d’accès (ACL) valides pour créer ou écrire des paramètres. Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Lecture et écriture dans le Registre](reading-from-and-writing-to-the-registry.md)
- [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md)

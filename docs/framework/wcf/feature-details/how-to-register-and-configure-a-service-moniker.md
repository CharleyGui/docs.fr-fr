---
title: 'Comment : inscrire et configurer un moniker de service'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: c68ca0f7c95515a0552b7003454dd87804176d3d
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212216"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Comment : inscrire et configurer un moniker de service
Avant d’utiliser le moniker de service Windows Communication Foundation (WCF) dans une application COM avec un contrat typé, vous devez inscrire les types avec attributs requis avec COM et configurer l’application COM et le moniker avec la liaison requise. configuré.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Pour inscrire les types avec attributs requis avec COM  
  
1. Utilisez l’outil [ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour récupérer le contrat de métadonnées du service WCF. Cela génère le code source pour un assembly client WCF et un fichier de configuration d’application cliente.  
  
2. Vérifiez que les types dans l'assembly sont marqués comme `ComVisible`. Pour cela, ajoutez l'attribut suivant au fichier AssemblyInfo.cs dans votre projet Visual Studio.  
  
    ```csharp
    [assembly: ComVisible(true)]  
    ```  
  
3. Compilez le client WCF managé comme un assembly avec nom fort. Cette procédure requiert une signature à l'aide d'une paire de clés de chiffrement. Pour plus d’informations, consultez [Signature d’un assembly avec un nom fort](../../../standard/assembly/sign-strong-name.md).  
  
4. Utilisez l'outil Assembly Registration Tool (Regasm.exe) avec l'option `/tlb` pour inscrire les types dans l'assembly avec COM.  
  
5. Utilisez l'outil Global Assembly Cache Tool (Gacutil.exe) pour ajouter l'assembly au Global Assembly Cache.  
  
    > [!NOTE]
    > La signature de l'assembly et son ajout au Global Assembly Cache sont deux étapes facultatives, mais elles peuvent simplifier le processus de chargement de l'assembly à partir de l'emplacement approprié au moment de l'exécution.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Pour configurer l’application COM et le moniker à l’aide des paramètres de liaison requis  
  
- Placez les définitions de liaison (générées par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dans le fichier de configuration de l’application cliente générée) dans le fichier de configuration de l’application cliente. Par exemple, pour un fichier exécutable Visual Basic 6.0 nommé CallCenterClient.exe, la configuration doit être placée dans un fichier nommé CallCenterConfig.exe.config, dans le même répertoire que le fichier exécutable. L'application cliente peut maintenant utiliser le moniker. Notez que la configuration de liaison n’est pas requise si vous utilisez l’un des types de liaison standard fournis par WCF.  
  
     Le type suivant est inscrit.  
  
    ```csharp  
    using System.ServiceModel;  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     L’application est exposée à l’aide d’une liaison `wsHttpBinding`. Pour une configuration de type et d'application donnée, les exemples de chaînes de moniker suivants sont utilisés.  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Vous pouvez utiliser l'une ou l'autre de ces chaînes de moniker à partir de l'application Visual Basic 6.0, après avoir ajouté une référence à l'assembly qui contient les types `IMathService`, tel qu'indiqué dans l'exemple de code suivant.  
  
    ```vb
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Dans cet exemple, la définition de la configuration de liaison `Binding1` est stockée dans un fichier de configuration judicieusement nommé pour l’application cliente, par exemple vb6nomapp.exe.config.  
  
    > [!NOTE]
    > Vous pouvez utiliser un code semblable dans une application C#, C++ ou d'un autre langage .NET.  
  
    > [!NOTE]
    > Si le moniker est incorrect ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur de type « Syntaxe non valide ». Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
     Bien que cette rubrique se concentre sur l’utilisation du moniker de service à partir du code Visual Basic 6,0, vous pouvez utiliser un moniker de service à partir d’autres langages. Lors de l'utilisation d'un moniker à partir du code C++, l'assembly généré par Svcutil.exe doit être importé avec le paramètre « no_namespace named_guids raw_interfaces_only », tel qu'indiqué dans le code suivant.  
  
    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Cela modifie les définitions d'interface importées afin que toutes les méthodes retournent un `HResult`. Toutes les autres valeurs de retour sont converties en paramètres de sortie. L'exécution globale des méthodes reste la même. Cela vous permet de déterminer la cause d'une exception lorsque vous appelez une méthode sur le proxy. Cette fonctionnalité n'est disponible qu'à partir du code C++.  
  
## <a name="see-also"></a>Voir aussi

- [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

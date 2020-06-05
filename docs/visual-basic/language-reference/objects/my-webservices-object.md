---
title: My.WebServices, objet
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a52f9f5f5b044273a45da5ef9478e2212def57a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372360"
---
# <a name="mywebservices-object"></a>My.WebServices, objet
Fournit des propriétés pour la création et l’accès à une instance unique de chaque service Web XML référencé par le projet actuel.  
  
## <a name="remarks"></a>Notes  
 L’objet `My.WebServices` fournit une instance de chaque service web référencé par le projet actuel. Chaque instance est instanciée sur demande. Vous pouvez accéder à ces services web via les propriétés de l’objet `My.WebServices`. La propriété porte le même nom que le service web auquel elle accède. Toute classe qui hérite de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> est un service web. Pour plus d’informations sur l’ajout de services Web à un projet, consultez [accès aux services Web d’application](../../developing-apps/programming/accessing-application-web-services.md).  
  
 L' `My.WebServices` objet expose uniquement les services Web associés au projet actif. Elle ne fournit pas l’accès aux services Web déclarés dans les dll référencées. Pour accéder à un service Web fourni par une DLL, vous devez utiliser le nom qualifié du service Web, sous la forme *DllName*. *WebServiceName*. Pour plus d’informations, consultez [accès aux services Web d’application](../../developing-apps/programming/accessing-application-web-services.md).  
  
 L’objet et ses propriétés ne sont pas disponibles pour les applications Web.  
  
## <a name="properties"></a>Propriétés  
 Chaque propriété de l' `My.WebServices` objet permet d’accéder à une instance d’un service Web référencé par le projet actuel. Le nom de la propriété est le même que le nom du service Web auquel la propriété accède, et le type de propriété est le même que le type du service Web.  
  
> [!NOTE]
> En cas de collision de nom, le nom de la propriété pour accéder à un service Web est *RootNamespace*_*namespace* \_ *ServiceName*. Par exemple, considérez deux services Web nommés `Service1` . Si l’un de ces services se trouve dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1` , vous accédez à ce service à l’aide de `My.WebServices.WindowsApplication1_Namespace1_Service1` .  
  
 Lorsque vous accédez pour la première fois à l’une des propriétés de l' `My.WebServices` objet, il crée une nouvelle instance du service Web et le stocke. Les accès ultérieurs de cette propriété retournent cette instance du service Web.  
  
 Vous pouvez supprimer un service Web en l’affectant `Nothing` à la propriété de ce service Web. L’accesseur Set de propriété assigne `Nothing` à la valeur stockée. Si vous assignez une valeur autre que `Nothing` à la propriété, la méthode setter lève une <xref:System.ArgumentException> exception.  
  
 Vous pouvez tester si une propriété de l' `My.WebServices` objet stocke une instance du service Web à l’aide de l' `Is` `IsNot` opérateur or. Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing` .  
  
> [!NOTE]
> En règle générale, l' `Is` `IsNot` opérateur or doit lire la valeur de la propriété pour effectuer la comparaison. Toutefois, si la propriété est actuellement stockée `Nothing` , la propriété crée une nouvelle instance du service Web, puis retourne cette instance. Toutefois, le compilateur Visual Basic traite les propriétés de l' `My.WebServices` objet de manière spéciale, et `Is` permet `IsNot` à l’opérateur ou de vérifier l’état de la propriété sans modifier sa valeur.  
  
## <a name="example"></a>Exemple  
 Cet exemple appelle la `FahrenheitToCelsius` méthode du `TemperatureConverter` service Web XML et retourne le résultat.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Pour que cet exemple fonctionne, votre projet doit faire référence à un service Web nommé `Converter` , et ce service Web doit exposer la `ConvertTemperature` méthode. Pour plus d’informations, consultez [accès aux services Web d’application](../../developing-apps/programming/accessing-application-web-services.md).  
  
 Ce code ne fonctionne pas dans un projet d’application Web.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="availability-by-project-type"></a>Disponibilité par type de projet  
  
|Type de projet|Disponible|  
|---|---|  
|Application Windows|**Oui**|  
|Bibliothèque de classes|**Oui**|  
|Application console|**Oui**|  
|Bibliothèque de contrôles Windows|**Oui**|  
|Bibliothèque de contrôles Web|**Oui**|  
|Service Windows|**Oui**|  
|Site web|Non|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Accès aux services web d’application](../../developing-apps/programming/accessing-application-web-services.md)

---
title: 'Exemple de fichier XSD : Schéma d’ordre d’achat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6680c9ca768dcb551d98cc9c393f8e5c59500794
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938096"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>Exemple de fichier XSD : Schéma d'ordre d'achat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Le fichier XSD suivant est utilisé dans différents exemples de la documentation du Concepteur de schémas XSD. Ce fichier est un schéma de bon de commande.  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
          elementFormDefault="qualified">  
  <xsd:element name='comment' type='xsd:string'/>  
  
  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>  
  
  <xsd:complexType name='USAddress'>  
    <xsd:annotation>  
      <xsd:documentation>  
        Purchase order schema for Example.Microsoft.com.  
      </xsd:documentation>  
    </xsd:annotation>  
    <xsd:sequence>  
      <xsd:element name='name'   type='xsd:string'/>  
      <xsd:element name='street' type='xsd:string'/>  
      <xsd:element name='city'   type='xsd:string'/>  
      <xsd:element name='state'  type='xsd:string'/>  
      <xsd:element name='zip'    type='xsd:decimal'/>  
    </xsd:sequence>  
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>  
  </xsd:complexType>  
  
  <xsd:simpleType name='SKU'>  
    <xsd:restriction base='xsd:string'>  
      <xsd:pattern value='\d{3}\w{3}'/>  
    </xsd:restriction>  
  </xsd:simpleType>  
  
  <xsd:complexType name='Items'>  
    <xsd:sequence>  
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name='productName' type='xsd:string'/>  
            <xsd:element name='quantity'>  
              <xsd:simpleType>  
                <xsd:restriction base='xsd:positiveInteger'>  
                  <xsd:minInclusive value='1'/>  
                  <xsd:maxExclusive value='100'/>  
                </xsd:restriction>  
              </xsd:simpleType>  
            </xsd:element>  
            <xsd:element name='USPrice'  type='xsd:decimal'/>  
            <xsd:element ref='tns:comment'/>  
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>  
          </xsd:sequence>  
          <xsd:attribute name='partNum' type='tns:SKU'/>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  
  <xsd:complexType name='PurchaseOrderType'>  
    <xsd:sequence>  
      <xsd:element name='shipTo' type='tns:USAddress'/>  
      <xsd:element name='billTo' type='tns:USAddress'/>  
      <xsd:element ref='tns:comment' minOccurs='0'/>  
      <xsd:element name='items'  type='tns:Items'/>  
    </xsd:sequence>  
    <xsd:attribute name='orderDate' type='xsd:date'/>  
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>  
  </xsd:complexType>  
</xsd:schema>  
```

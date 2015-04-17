---
weight: 1
layout: default
category: trackmaster
language: en
title: index
version: v2
---


# {{ page.title }}




###  An online advertising measurement tool ###

## Main TrackMaster API Objects

**TrackMaster™ Network** for Advertisers designed for advertisers, or advertising agencies,to organize a web ad campaign and track serving data and user interactions.

　　

**Network**  

The Network is the root object of all data for a specific network. Most customers have only one network, although a few large customers have two or three. Each network manages its own user accounts and permissions; you must have an account and permissions for each network on which you want to make calls.


**Network User/Roles**  

Networks manage its own user accounts and permissions. The permissions to perform certain operations are assigned to specific roles. Network User/Roles are assigned particular roles, and through those role assignments acquire the permissions to perform particular functions. Since Network User/Roles are not assigned permissions directly, but only acquire them through their role. Certainly, you can allot special permissions to individual.
　　
**Media** 

TrackMaster API maintains a global list of Media, called the Media Lib, with entries that describe each media’s information. 

\* If a media you want to include in your local list is not present in the Media Lib, you can contact us.

**Advertiser**  

TrackMaster API maintains a global list of Advertisers, called the Advertisers Lib, with entries that describe each advertisers’ information. 

**Brand**  

Part of advertisers has one or more Brands objects associated with it. A brand is a brand that is associated with an independent product line. A brand can belong to one advertiser only.

**Campaign**  

Each advertiser has one or more Campaign objects associated with it. A campaign groups together a set of ads and placements for a single advertiser. Campaigns have a start and end date. A campaign can belong to one advertiser only. A campaign links to one or more Placement.

**Placement**  

A Placement represents a fixed block of ad space on a page. A creative is an advertisement, and a placement holds a creative. A placement provides the creative’s URL, its physical dimensions, pricing information such as CPM, CPC, and a few other properties. Placements can optionally be grouped into a PlacementGroup for media that sell placements in groups.

**Creative**

A creative is a wrapper for one or more files representing the advertisement. You can assign a default creative to multiple Ad objects from any campaign in your account.


## Agency ##

* [Agency develop guide](/doc/trackmaster/v2/en/agency.html)

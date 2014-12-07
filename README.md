# SwiftAddressBook - A strong-typed Swift Wrapper for ABAddressBook

Complete wrapper for the ABAddressBook C-Framework for iOS, written in Swift to be typesafe and convenient

## Description

  It is tedious and requires very much reading in the documentation if you want to understand the ABAddressBook in iOS. To provide a solution, this wrapper uses Swift, which is strong-typed (unlike c). It also circumvents the use of unsafe c-pointers when accessing ABAddressBook from Swift, by directly casting them to the correct type. All properties, previously only available via the correct key, can now be accessed conveniently via variables.
  
  Here´s how you would access ABAddressBook via SwiftAddressBook:
  
  Request access
  
    swiftAddressBook?.requestAccessWithCompletion({ (success, error) -> Void in
        if success {
          //do something with swiftAddressBook
        }
        else {
          //no success. Optionally evaluate error
        }
      })
  
  Use Addressbook (e.g. get array of all people and log their phone numbers)
  
    if let people = swiftAddressBook?.allPeople {
      for person in people {
        //person.phoneNumbers is a "multivalue" entry
        //so you get an array of MultivalueEntrys
        //see MultivalueEntry in SwiftAddressBook
        NSLog("%@", person.phoneNumbers?.map( {$0.value} ))
      }
    }
  
  Complicated Swift typecasting to NS-..., thousand times of unwrapping optionals, figuring out which constant is the key to your person property, distinguishing between group, source or person - nothing that you have to deal with any more

## License  
    Copyright (C) 2014  Socialbit GmbH
    
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.
    
    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.
    
    You should have received a copy of the GNU General Public License
    along with this program.  If not, see http:www.gnu.org/licenses/ .
    
    If you would to like license this software for non-free commercial use,
    please write us at kontakt@socialbit.de .

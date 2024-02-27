IP Calculator
=============

Overview
--------

The IP Calculator is a powerful TypeScript library that simplifies the process of calculating various network details based on a given IP address and subnet mask. It offers a wide range of methods to set and validate the IP address and subnet mask, and calculate important network properties such as the network address, broadcast address, wildcard mask, first and last IP addresses, IPv4 class, number of hosts and networks, and the netmask in dot-decimal notation.

Usage
-----

To get started with the IP Calculator, follow these simple steps:

1. Import the `Calculator` class:
```typescript
import { Calculator } from './calculator';
```
2. Create a new instance of the class by passing in an object with the `ip` and `mask` properties:
```typescript
const calc = new Calculator({ ip: '192.168.1.1', mask: 24 });
```
Alternatively, you can use the `setIp` and `setMask` methods to set the IP address and subnet mask:
```typescript
const calc = new Calculator()
  .setIp('192.168.1.1')
  .setMask(24);
```
3. Call the `calculate` method to calculate the network details:
```typescript
calc.calculate();
```
4. Access the calculated values through the following properties:

* `ip`: the IP address in dot-decimal notation
* `network`: the network address in dot-decimal notation
* `ipv4Class`: the IPv4 class (A, B, C, D, or E)
* `maxHosts`: the maximum number of hosts in the network
* `maxNetworks`: the maximum number of networks
* `wildcard`: the wildcard mask in dot-decimal notation
* `hostMin`: the first IP address in the network
* `hostMax`: the last IP address in the network
* `netmask`: the netmask in dot-decimal notation
* `broadcast`: the broadcast address in dot-decimal notation
* `mask`: the subnet mask in dot-decimal notation



Example
-------

Here's an example of how to use the IP Calculator to calculate the network details for the IP address `192.168.1.1` with a subnet mask of `24`:
```typescript
import { Calculator } from './calculator';

const calc = new Calculator({ ip: '192.168.1.1', mask: '255.255.127.0' });
calc.calculate();

console.log(calc.ip); // 192.168.1.1
console.log(calc.network); // 192.168.1.0
console.log(calc.ipv4Class); // C
console.log(calc.maxHosts); // 254
console.log(calc.maxNetworks); // 1
console.log(calc.wildcard); // 0.0.0.255
console.log(calc.hostMin); // 192.168.1.1
console.log(calc.hostMax); // 192.168.1.254
console.log(calc.netmask); // 255.255.255.0
console.log(calc.broadcast); // 192.168.1.255
console.log(calc.mask); // 24
```

Constructor
-----------

The `Calculator` class can be instantiated with an optional `options` parameter, which is an object that can contain the following properties:

* `ip`: A string representing the IP address to be used for the calculator. The string should be in the standard dot-decimal notation (e.g. "192.168.1.1"). This property is optional, and if it is not provided, an empty string will be used as the default value

* `mask`: A number or string representing the subnet mask to be used for the calculator. If the mask is a number, it should be the number of bits in the mask (e.g. 24 for a Class C network). If the mask is a string, it should be in the standard dot-decimal notation (e.g. "255.255.255.0"). This property is optional, and if it is not provided, 0 will be used as the default value.

Chainable methods
-----------------

You can also use the `setIp` and `setMask` methods to set the IP address and subnet mask respectively, after instantiating the class. These methods take a single argument, which is a string representing the IP address or subnet mask in the standard dot-decimal notation.

The `calculate` method of the class does not take any parameters, it uses the ip and mask set by the constructor or the setter methods to calculate the network details.

All these methods are chainable, meaning that you can call multiple methods on the same instance of the class in a single statement, like this:
```typescript
const calculator = new Calculator()
  .setIp('10.0.0.1')
  .setMask(24)
  .calculate();
```
This is known as the builder pattern.

Helpers
-------

The `Calculator` class also includes two helper methods to convert IP addresses to binary or hexadecimal notation:

* `convertToBinary(ip: string): string`: converts an IP address in dot-decimal notation to binary notation.
* `convertToHexa(ip: string): string`: converts an IP address in dot-decimal notation to hexadecimal notation.


```typescript
import { Calculator } from './calculator';

const calc = new Calculator({ ip: '192.168.1.1', mask: '255.255.127.0' });
calc.calculate();

console.log(calc.convertToBinary(calc.ip)); // 11000000.10101000.00000001.00000001
console.log(calc.convertToHexa(calc.ip)); // c0a80101
```
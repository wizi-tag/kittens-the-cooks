```ts
// Tags: Generic, Enum ('small' | 'large' | 'medium'), 
// Union, Interface, implements

enum Size {
  small = 'small',
  large = 'large',
  medium = 'medium'
}

interface ShopInterface {
  items:ShopType[];
  addGood(item: ShopType): number;
}

class Shop implements ShopInterface {
  items:ShopType[] = [];

  addGood(item: ShopType) {
    return this.items.push(item);
  }

  get goods(): ShopType[] {
    return this.items;
  }
}

interface Product {
  name: string;
  price: number;
  discount: number;
}

class BaseProduct implements Product {
  name: string;

  price: number;

  discount: number;

  constructor(name: string, price: number, discount: number) {
    this.name = name;
    this.price = price;
    this.discount = discount;
  }
}

class Banana extends BaseProduct {
  size: Size;

  constructor(price: number, discount: number, size: Size) {
    super('banan', price, discount);
    this.size = size;
  }
}

class IceCream extends BaseProduct {
  withGlace: boolean;

  constructor(price: number, discount: number, withGlace: boolean) {
    super('iceCream', price, discount);
    this.withGlace = withGlace;
  }
}

type ShopType = Banana | IceCream;

const shop: Shop = new Shop();

const iceCream: IceCream = new IceCream(10, 0, true);
const banana: Banana = new Banana(5, 0.1, Size.small);

shop.addGood(iceCream);
shop.addGood(banana);

console.log(shop.goods);
```
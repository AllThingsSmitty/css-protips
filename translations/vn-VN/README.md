<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Một bộ gồm những tips để giúp kỹ năng CSS trở nên pro

> For other great lists check out [@sindresorhus](https://github.com/sindresorhus/)'s curated list of [awesome lists](https://github.com/sindresorhus/awesome/).


## Table of Contents

* [Protips](#protips)
* [Support](#support)
* [Translations](#translations)
* [Contribution Guidelines](CONTRIBUTING.md)


## Protips

1. [Dùng CSS Reset](#dùng-css-reset)
1. [Thừa kế `box-sizing`](#thừa-kế-box-sizing)
1. [Dùng `unset` thay vì đặt lại tất cả thuộc tính](#use-unset-instead-of-resetting-all-properties)
1. [Dùng `:not()` để Áp dụng / Không áp dụng các đường viền trên Điều hướng](#dùng-not-de-ap-dung-khong-ap-dung-cac-duong-vien-tren-dieu-huong)
1. [Kiểm tra xem Phông chữ có được cài đặt cục bộ không](#check-if-font-is-installed-locally)
1. [Thêm `line-height` cho `body`](#add-line-height-to-body)
1. [Đặt `:focus` cho Form Elements](#set-focus-for-form-elements)
1. [Mọi thứ ở giữa theo chiều dọc](#vertically-center-anything)
1. [Danh sách được phân tách bằng dấu phẩy](#comma-separated-lists)
1. [Chọn nhiều items với Negative `nth-child`](#select-items-using-negative-nth-child)
1. [Dùng SVG cho Icons](#use-svg-for-icons)
1. [Sử dụng "Lobotomized Owl" Selector](#use-the-lobotomized-owl-selector)
1. [Dùng `max-height` cho thanh trượt CSS Sliders](#use-max-height-for-pure-css-sliders)
1. [Các ô trong bảng có chiều rộng bằng nhau](#equal-width-table-cells)
1. [Get Rid of Margin Hacks With Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Sử dụng Attribute Selectors với các liên kết trống](#use-attribute-selectors-with-empty-links)
1. [Style "Default" Links](#style-default-links)
1. [Consistent Vertical Rhythm](#consistent-vertical-rhythm)
1. [Intrinsic Ratio Boxes](#intrinsic-ratio-boxes)
1. [Hình ảnh bị vỡ](#style-broken-images)
1. [Dùng `rem` cho toàn cục; dùng `em` cho cục bộ](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Ẩn các video tự động phát không bị tắt tiếng](#hide-autoplay-videos-that-arent-muted)
1. [Dùng `:root` cho Flexible Type](#use-root-for-flexible-type)
1. [Để `font-size` trong Form Elements để có một trải nghiệm mobile tốt hơn](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [Dùng Pointer Events để kiểm soát mouse control](#use-pointer-events-to-control-mouse-events)
1. [Đặt `display: none` trên ngắt dòng được sử dụng làm khoảng cách](#set-display-none-on-line-breaks-used-as-spacing)


### Dùng CSS Reset

Css resets giúp thực thi tính nhất quán về kiểu dáng trên các trình duyệt khác nhau với một phương tiện chặn rõ ràng cho các yếu tố tạo kiểu.Bạn có thể sử dụng thư viện CSS Reset như [Normalize](http://necolas.github.io/normalize.css/),hoặc bạn có thể sử dụng phương pháp đặt lại đơn giản hơn:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Bây giờ các phần tử sẽ bị loại bỏ magins và padding, và `box-sizing` cho phép bạn quản lý bố cục bằng CSS box model.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Note:** Nếu bạn làm theo  [Inherit `box-sizing`](#inherit-box-sizing) mẹo dưới đây, bạn có thể chọn không bao gồm `box-sizing` thuộc tính trong CSS reset của bạn.

<sup>[back to table of contents](#table-of-contents)</sup>


### Thừa kế `box-sizing`

`box-sizing` được thừa kế từ `html`:

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

Điều này giúp bạn dễ dàng thay đổi `box-sizing` hơn trong các plugin hoặc các thành phần khác thúc đẩy hành vi khác.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[back to table of contents](#table-of-contents)</sup>


### Dùng `unset` thay vì đặt lại tất cả thuộc tính

Khi đặt lại thuộc tính của một phần tử, không cần thiết phải đặt lại từng thuộc tính riêng lẻ:

```css
button {
  background: none;
  border: none;
  color: inherit;
  font: inherit;
  outline: none;
  padding: 0;
}
```

Bạn có thể chỉ định tất cả các thuộc tính của một phần tử bằng cách sử dụng tất cả các viết tắt.  Đặt giá trị thành không đặt sẽ thay đổi thuộc tính của phần tử thành giá trị ban đầu của chúng:

```css
button {
  all: unset;
}
```

**Note:** `all` thì không được hỗ trợ trên IE11 và hiện đang được xem xét hỗ trợ trong Edge. `unset` thì cũng vậy.

<sup>[back to table of contents](#table-of-contents)</sup>


### Dùng `:not()` để Áp dụng / Không áp dụng các đường viền trên Điều hướng

Thay vì đặt trên border...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...và sau đó lấy nó ra khỏi phần tử cuối cùng...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...dùng `:not()` pseudo-class để chỉ áp dụng cho các phần tử bạn muốn:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Ở đây, CSS selector được đọc như một con người sẽ mô tả nó.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[back to table of contents](#table-of-contents)</sup>


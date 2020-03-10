# esc_pos_utils

Basic Flutter/Dart classes for ESC/POS printing.


## Getting started (Generate a simple ticket)

Check the complete example in `example/example.dart`

```dart
final Ticket ticket = Ticket(PaperSize.mm80);

ticket.text('Hello world!');
ticket.text('Bold text', styles: PosStyles(bold: true));
ticket.text('Reverse text', styles: PosStyles(reverse: true));
ticket.text('Underlined text',
    styles: PosStyles(underline: true), linesAfter: 1);

ticket.text('Align left', styles: PosStyles(align: PosTextAlign.left));
ticket.text('Align center', styles: PosStyles(align: PosTextAlign.center));
ticket.text('Align right',
    styles: PosStyles(align: PosTextAlign.right), linesAfter: 1);

ticket.row([
    PosColumn(
        text: 'col3',
        width: 3,
        styles: PosStyles(align: PosTextAlign.center, underline: true),
    ),
    PosColumn(
        text: 'col6',
        width: 6,
        styles: PosStyles(align: PosTextAlign.center, underline: true),
    ),
    PosColumn(
        text: 'col3',
        width: 3,
        styles: PosStyles(align: PosTextAlign.center, underline: true),
    ),
]);

ticket.text('Text size 200%',
    styles: PosStyles(
    height: PosTextSize.size2,
    width: PosTextSize.size2,
    ));

// Print barcode
final List<int> barData = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 4];
ticket.barcode(Barcode.upcA(barData));

ticket.feed(2);
ticket.cut();
```
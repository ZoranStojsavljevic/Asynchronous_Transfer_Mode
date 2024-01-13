## ATM Adaptation Layer 5
* [ATM Adaptation Layer 5](https://en.wikipedia.org/wiki/ATM_Adaptation_Layer_5)

ATM Adaptation Layer 5 (AAL5) is an ATM adaptation layer used to
send variable-length packets up to 65,535 octets in size across
an Asynchronous Transfer Mode (ATM) network.

Unlike most network frames, which place control information
in the header, AAL5 places control information in an 8-octet
trailer at the end of the packet. The AAL5 trailer contains a
16-bit length field, a 32-bit cyclic redundancy check (CRC) and
two 8-bit fields labeled UU and CPI that are currently unused.

Each AAL5 packet is divided into an integral number of ATM
cells and reassembled into a packet before delivery to the
receiving host. This process is known as Segmentation And
Reassembly (SAR). The last cell contains padding to ensure that
the entire packet is a multiple of 48 octets long. The final
cell contains up to 40 octets of data, followed by padding bytes
and the 8-octet trailer. In other words, AAL5 places the trailer
in the last 8 octets of the final cell where it can be found
without knowing the length of the packet; the final cell is
identified by a bit in the ATM header (see below), and the
trailer is always in the last 8 octets of that cell.

### Convergence, segmentation, and reassembly

When an application sends data over an ATM connection using
AAL5, the host delivers a block of data to the AAL5 interface.
AAL5 generates a trailer, divides the information into 48-octet
pieces, and transfers each piece across the ATM network in a
single cell. On the receiving end of the connection, AAL5
reassembles incoming cells into a packet, checks the CRC to
ensure that all pieces arrived correctly, and passes the
resulting block of data to the host software. The process of
dividing a block of data into cells and regrouping them is
known as ATM Segmentation And Reassembly (SAR).

By separating the functions of segmentation and reassembly from
cell transport, AAL5 follows the layering principle. The ATM
cell transfer layer is classified as "machine-to-machine"
because the layering principle applies from one machine to the
next (e.g., between a host and a switch or between two switches).
The AAL5 layer is classified as "end-to-end" because the layering
principle applies from the source to the destination - AAL5
presents the receiving software with data in exactly the same
size blocks as the application passed to the AAL5 on the sending
end.

The AAL5 on the receiving side knows how many cells comprise a
packet because the sending AAL5 uses the low-order bit of the
"PAYLOAD TYPE" field of the ATM cell header to mark the final
cell in a packet. This final cell header can be thought of as an
"end-to-end bit". Thus, the receiving AAL5 collects incoming
cells until it finds one with an end-of-packet bit set. ATM
standards use the term "convergence" to describe mechanisms that
recognize the end of a packet. Although AAL5 uses a single bit
in the cell header for convergence, other ATM adaptation layer
protocols are free to use other convergence mechanisms.

### Literature
* [ATM-AAL5_print.pdf](http://ebook.pldworld.com/_Semiconductors/Motorola/Embedded_Learning_Center/ELC/CDV340CT/Rev.0/module24524/mod11_FCC_ATM-AAL5_print.pdf)

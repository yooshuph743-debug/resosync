import React, { useState } from "react";
          </CardContent>
        </Card>
      )}

      {/* ADD ITEM */}
      {isAdmin && (
        <Card className="mb-4">
          <CardContent className="p-4 space-y-2">
            <h3 className="font-semibold">Add Rental Item</h3>
            <Input
              placeholder="Item Title"
              value={itemForm.title}
              onChange={(e) => setItemForm({ ...itemForm, title: e.target.value })}
            />
            <Input
              placeholder="Price per day"
              value={itemForm.price}
              onChange={(e) => setItemForm({ ...itemForm, price: e.target.value })}
            />
            <Button onClick={addItem}>Add Item</Button>
          </CardContent>
        </Card>
      )}

      {/* BOOKING FORM */}
      <Card className="mb-4">
        <CardContent className="p-4 space-y-2">
          <h3 className="font-semibold">Book Item</h3>
          <Input
            placeholder="Your Name"
            value={bookingForm.name}
            onChange={(e) => setBookingForm({ ...bookingForm, name: e.target.value })}
          />
          <Input
            placeholder="Phone number (optional for contact)"
            value={bookingForm.phone}
            onChange={(e) => setBookingForm({ ...bookingForm, phone: e.target.value })}
          />
        </CardContent>
      </Card>

      {/* ITEMS */}
      <Card>
        <CardContent className="p-4">
          <h3 className="font-semibold mb-2">Available Items</h3>

          <div className="grid gap-2">
            {items.map((item) => (
              <div key={item.id} className="border p-2 rounded">
                <p className="font-bold">{item.title}</p>
                <p>MVR {item.price}/day</p>
                <p>Status: {item.available ? "Available" : "Not Available"}</p>

                <Button className="mt-2" onClick={() => bookItem(item)}>
                  Book Now
                </Button>

                {isAdmin && (
                  <Button className="mt-2 ml-2" onClick={() => toggleAvailability(item.id)}>
                    Toggle
                  </Button>
                )}
              </div>
            ))}
          </div>
        </CardContent>
      </Card>

      {/* BOOKINGS */}
      {isAdmin && (
        <Card className="mt-4">
          <CardContent className="p-4">
            <h3 className="font-semibold">Bookings</h3>
            {bookings.map((b) => (
              <div key={b.id} className="border p-2 mt-2 rounded">
                <p>Booking ID: {b.id}</p>
                <p>Item: {b.itemName}</p>
                <p>Guest: {b.guestName}</p>
                <p>Phone: {b.guestPhone || "Not provided"}</p>
                <p>Status: {b.status}</p>
              </div>
            ))}
          </CardContent>
        </Card>
      )}
    </div>
  );
}

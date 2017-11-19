License regarding output code
=============================

Really short version
====================

The output from pyxie - is for yours to do with as you like.
This document tries to make sure this unamiguous.

Longer version
==============

While musing random stuff, things like Bison sprang to mind. Bison is a
GPL'd parser generator, and placed restrctions over its output. This
led to all sorts of questions over time, and so on. In the case of Pyxie,
I want to avoid those questions. They will frusrate me, and frustrate you
for zero benefit.

So, to be clear, I view the output of pyxie to be yours. You wrote the
source that Pyxie transforms, and the transformed code is a derivative
of your code. Therefore the output from pyxie is your code, generally.

As a result, in files /directly/ derived from your code the following
statement is included at the top:

    //
    // This file contains code generated by Pyxie - http://www.sparkslabs.com/pyxie
    //
    // This file is derived from the user's source code, copyright resides
    // with the author of the user's source code.
    //
    // You can edit this header in any way suitable for your project
    //

There will always be elements though that are actually parts of pyxie that
get copied into your code as part of that transformation. An example would
include things like how python iterators and generators are implemented.

Clearly I'm not going to assign copyright over those bits of code to you.
Therefore I need to give you a license for those.

As a result, in files that are essentially derived from Pyxie, the following
statement is included at the top:

    //
    // This file contains code generated by Pyxie - http://www.sparkslabs.com/pyxie
    //
    // This file contains parts of code derived from Pyxie itself. It may be used
    // under the following terms:
    //
    // Permission is hereby granted, free of charge, to any person obtaining
    // a copy of this software and associated documentation files (the "Software"),
    // to deal in the Software without restriction, including without limitation
    // the rights to use, copy, modify, merge, publish, distribute, sublicense,
    // and/or sell copies of the Software, and to permit persons to whom the Software
    // is furnished to do so, subject to the following conditions:
    //
    // THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    // IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    // FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    // AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    // LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    // OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    // SOFTWARE.
    //
    // For more information see: http://www.sparkslabs.com/pyxie/COPYING.output.md
    //

Note: this is a more permissive version of the MIT license. It's more permissive
because it actually allows you to remove the notice. If you're distributing your
source to others though, this probably wouldn't be a good idea.


Worked example
==============

Pyxie is in essence a code generator. It takes a definition - such as something like this:

    #include <Adafruit_NeoPixel.h>

    pin = 6
    number_of_pixels = 16
    delayval = 500

    pixels = Adafruit_NeoPixel(number_of_pixels, pin, NEO_GRB + NEO_KHZ800)

    pixels.begin()

    while True:
        for i in range(number_of_pixels):
            pixels.setPixelColor(i, pixels.Color(0,150,0))
            pixels.show()
            delay(delayval)

And generates a main file like this:

    //
    // This file contains code generated by Pyxie - http://www.sparkslabs.com/pyxie
    //
    // This file is derived from the user's source code, copyright resides
    // with the author of the user's source code.
    //
    // You can edit this header in any way suitable for your project
    //

    #include <Adafruit_NeoPixel.h>

    #include "iterators.cpp"

    void setup() {
        int delayval;
        int i;
        int number_of_pixels;
        int pin;
        Adafruit_NeoPixel pixels;
        range range_iter_1;

        pin = 6;
        number_of_pixels = 16;
        delayval = 500;
        pixels = Adafruit_NeoPixel(number_of_pixels, pin, (NEO_GRB + NEO_KHZ800));
        (pixels).begin();
        while (true) {

            range_iter_1 = range(number_of_pixels);
            while (true) {
                i = range_iter_1.next();
                if (range_iter_1.completed())
                    break;


                (pixels).setPixelColor(i, (pixels).Color(0, 150, 0));
                (pixels).show();
                delay(delayval);    // Itself uses i
            }
            ;
        };
    }

    void loop() {
    }

You'll note though that the output code includes code from Pyxie itself - iterators.cpp
and iterators.hpp. These aren't written by you and need a license. As a result the
output of these looks like this:

iterators.cpp:

    //
    // This file contains code generated by Pyxie - http://www.sparkslabs.com/pyxie
    //
    // This file contains parts of code derived from Pyxie itself. It may be used
    // under the following terms:
    //
    // Permission is hereby granted, free of charge, to any person obtaining
    // a copy of this software and associated documentation files (the "Software"),
    // to deal in the Software without restriction, including without limitation
    // the rights to use, copy, modify, merge, publish, distribute, sublicense,
    // and/or sell copies of the Software, and to permit persons to whom the Software
    // is furnished to do so, subject to the following conditions:
    //
    // THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    // IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    // FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    // AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    // LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    // OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    // SOFTWARE.
    //
    // For more information see: http://www.sparkslabs.com/pyxie/COPYING.output.md
    //

    #include "iterators.hpp"

    struct range : public Generator<int> {
        int start;
        int end;
        int step;

        int index;

        range() :                                start(0),     end(0),   step(1), index(0)            {     };
        range(int end) :                         start(0),     end(end), step(1), index(0)            {     };
        range(int start, int end)     :          start(start), end(end), step(1), index(start)        {     };
        range(int start, int end, int stepsize): start(start), end(end), step(stepsize), index(start) {     };
        ~range() {     };

        virtual int next() {
            GENERATOR_START

            while ( step>0  ? index < end : index > end) {
                YIELD(index);
                index = index + step;
            }

            GENERATOR_END
        }
    };

iterators.hpp looks like this:

    #ifndef PYXIE_ITERATORS_HPP
    #define PYXIE_ITERATORS_HPP

    //
    // This file contains code generated by Pyxie - http://www.sparkslabs.com/pyxie
    //
    // This file contains parts of code derived from Pyxie itself. It may be used
    // under the following terms:
    //
    // Permission is hereby granted, free of charge, to any person obtaining
    // a copy of this software and associated documentation files (the "Software"),
    // to deal in the Software without restriction, including without limitation
    // the rights to use, copy, modify, merge, publish, distribute, sublicense,
    // and/or sell copies of the Software, and to permit persons to whom the Software
    // is furnished to do so, subject to the following conditions:
    //
    // THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    // IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    // FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    // AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    // LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    // OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    // SOFTWARE.
    //
    // For more information see: http://www.sparkslabs.com/pyxie/COPYING.output.md
    //

    /*
    * Python Style Iterators in C++, based in part on experiment work in Kamaelia
    * Redone to remove use of generators, so that this can be used on Arduino
    * 
    */

    #define GENERATOR_START if (this->__generator_state == -1) { return __default_value; } switch(this->__generator_state) { default:
    #define YIELD(value)    this->__generator_state = __LINE__; return ((value) );   case __LINE__:
    #define GENERATOR_END    }; this->__generator_state = -1; return __default_value;

    template<class T>
    struct Iterator {
        virtual T next()=0;
        virtual bool completed()=0;
    };

    template<class T>
    class Generator : public Iterator<T> {
    protected:
        int __generator_state;
    public:
        T __default_value;
        Generator() : __default_value(T()) {     };
        ~Generator() {     };
        virtual bool completed() { return __generator_state==-1; };
    };

    #endif


Why?
====

In Pyxie I make pains to try and make the output code readable (within reason).
The reason for this is simple you may decide to stop using pyxie if you hit the
limits of the language and to continue to proceed using the output code. The
reason for this is because I'm a pragmatist :-)

In that situation you don't want to be in the situation where you suddenly can't
use the code in ways that you want to. I wouldn't want that for me, so it wouldn't
be right for me to expect that from you. Hence this explicit licensing over
output files.


Open Source
===========

All that said, consider this:

* Pyxie is open source so, if possible, consider leaving code you create
  using pyxie open source,

* If you can't and you make a profit in anyway, consider making a donation
  to the pyxie project, to help run servers, boost morale etc.

Failing that, a christmas (or similar) card would be nice - but of course none
of this is obligatory :)

Enjoy :-)


Michael, December 2016
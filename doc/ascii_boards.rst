The :mod:`!ascii_boards` module
-------------------------------

.. module:: sgfmill.ascii_boards
   :synopsis: ASCII Go board diagrams.

The :mod:`!sgfmill.ascii_boards` module contains functions for producing and
interpreting ASCII diagrams of Go board positions.

It supports square boards up to size 25x25, which is the upper limit of the
notation it uses (and also the upper limit for |gtp|).


.. function:: render_board(board)

   :rtype: string

   Returns an ASCII diagram of the position on the :class:`.Board` *board*.

   The returned string does not end with a newline.

   ::

      >>> b = boards.Board(9)
      >>> b.play(2, 5, 'b')
      >>> b.play(3, 6, 'w')
      >>> print(ascii_boards.render_board(b))
      9  .  .  .  .  .  .  .  .  .
      8  .  .  .  .  .  .  .  .  .
      7  .  .  .  .  .  .  .  .  .
      6  .  .  .  .  .  .  .  .  .
      5  .  .  .  .  .  .  .  .  .
      4  .  .  .  .  .  .  o  .  .
      3  .  .  .  .  .  #  .  .  .
      2  .  .  .  .  .  .  .  .  .
      1  .  .  .  .  .  .  .  .  .
         A  B  C  D  E  F  G  H  J

   See also the :script:`show_sgf.py` example script.


.. function:: interpret_diagram(diagram, size[, board])

   :rtype: :class:`.Board`

   Returns the position given in an ASCII diagram.

   *diagram* should be a string in the format returned by
   :func:`render_board`, representing a position with the specified size.
   Leading and trailing whitespace is ignored.

   If the diagram is not in the right form, this function may raise
   :exc:`ValueError` or may return a 'best guess'.

   If the optional *board* parameter is provided, it must be an empty
   :class:`.Board` of the right size; the same object will be returned (this
   option is provided so you can use a different Board class).

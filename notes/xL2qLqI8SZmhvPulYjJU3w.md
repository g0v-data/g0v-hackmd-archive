import tensorflow as tf


A = tf.constant(50, name='const_A')
B = tf.constant(100, name='const_B')

with tf.Session() as sess:
   
    with tf.name_scope('Run'):
        B = sess.run(A+B)
    print(B)
    
   
   train_writer = tf.summary.FileWriter('/root/tfboard_Test', sess.graph)
    train_writer.close()

    
    $ tensorboard --logdir=/root/tfboard_Test


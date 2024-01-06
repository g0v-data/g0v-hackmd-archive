# Create a unique filename
                        if device_serial_number:
                            filename = 'Trigger_MultipleCamera-%s-%d.jpg' % (device_serial_number, n)
                        else:
                            filename = 'Trigger_MultipleCamera-%d-%d.jpg' % (i, n)
                        # Save image
                        image_result.Save(filename)
                        print('Image saved at %s' % filename)
# csdr Cheat Sheet

[csdr](https://github.com/ha7ilm/csdr) is a truly stunning command line software defined radio tool. The command set for csdr is very large and this can make it difficult to look up the commnad you want to use. This cheat sheet is intended to be a simple list that lets you look up commands more easily.

| command | description |
| ------- | ----------- |
| realpart_cf                       | It takes the real part of the complex signal, and throws away the imaginary part. |
| clipdetect_ff                     | It clones the signal (the input and the output is the same), but it prints a warning on stderr if any sample value is | out of the -1.0 ... 1.0 range. |
| limit_ff                          | The input signal amplitude will not be let out of the -max_amplitude ... max_amplitude range. |
| gain_ff                           | It multiplies all samples by gain. |
| clones                            | It copies the input to the output. |
| through                           | It copies the input to the output, while also displaying the data rate going through it. |
| none                              | The csdr process just exits with 0. |
| yes_f                             | It outputs continously the to_repeat float number. If buf_times is not given, it never stops. |
| detect_nan_ff                     | Along with copying its input samples to the output, it prints a warning message to stderr if it finds any IEEE floating point NaN values among the samples. |
| dump_f                            | It prints all floating point input samples as text. |
| dump_u8                           | It prints all input bytes as text, in hexadecimal form. |
| flowcontrol                       | It limits the data rate of a stream to a given data_rate number of bytes per second. |
| shift_math_cc                     | It shifts the signal in the frequency domain by rate. |
| shift_addition_cc                 | Operation is the same as for shift_math_cc. |
| shift_addition_cc_test            | This function was used to test the accuracy of the method above. |
| shift_table_cc                    | Operation is the same as with shift_math_cc. |
| shift_addfast_cc                  | Operation is the same as for shift_math_cc. |
| shift_unroll_cc                   | Operation is the same as for shift_math_cc. |
| decimating_shift_addition_cc      | It shifts the input signal in the frequency domain, and also decimates it, without filtering. It will be useful as a | part of the FFT channelizer implementation (to be done). |
| shift_addition_fc                 | It converts the real input signal to complex, and then shifts it in the frequency domain by rate. |
| dcblock_ff                        | This is a DC blocking IIR filter. |
| fastdcblock_ff                    | This is a DC blocker that works based on the average of the buffer. |
| fmdemod_atan_cf                   | It is an FM demodulator that internally uses the atan function in math.h, so it is not so fast. |
| fmdemod_quadri_cf                 | It is an FM demodulator that is based on the quadri-correlator method, and it can be effectively auto-vectorized, so | it should be faster. |
| fmdemod_quadri_novect_cf          | It has more easily understandable code than the previous one, but can't be auto-vectorized. |
| deemphasis_wfm_ff                 | It does de-emphasis with the given RC time constant tau. |
| deemphasis_nfm_ff                 | It does de-emphasis on narrow-band FM for communication equipment (e.g. two-way radios). |
| amdemod_cf                        | It is an AM demodulator that uses sqrt. On some architectures sqrt can be directly calculated by dedicated CPU instructions, but on others it may be slower. |
| amdemod_estimator_cf              | It is an AM demodulator that uses an estimation method that is faster but less accurate than amdemod_cf. |
| firdes_lowpass_f                  | Low-pass FIR filter design function to output real taps, with a cutoff_rate proportional to the sampling frequency, using the windowed sinc filter design method. |
| firdes_bandpass_c                 | Band-pass FIR filter design function to output complex taps. |
| fir_decimate_cc                   | It is a decimator that keeps one sample out of decimation_factor samples. |
| fir_interpolate_cc                | It is an interpolator that generates interpolation_factor number of output samples from one input sample. |
| rational_resampler_ff             | It is a resampler that takes integer values of interpolation and decimation. The output sample rate will be interpolation / decimation × input_sample_rate. |
| fractional_decimator_ff           | It can decimate by a floating point ratio. |
| old_fractional_decimator_ff       | This is the deprecated, old algorithm to decimate by a floating point ratio, superseded by fractional_decimator_ff. |
| bandpass_fir_fft_cc               | It performs a bandpass FIR filter on complex samples, using FFT and the overlap-add method. |
| agc_ff                            | It is an automatic gain control function. |
| fastagc_ff                        | It is a faster AGC that linearly changes the gain, taking the highest amplitude peak in the buffer into consideration. Its output will never exceed -reference ... reference. |
| fft_cc                            | It performs an FFT on the first fft_size samples out of out_of_every_n_samples, thus skipping out_of_every_n_samples - fft_size samples in the input. |
| fft_fc                            | It works similarly to fft_cc, but on real input samples. |
| fft_benchmark                     | It measures the time taken to process fft_cycles transforms of fft_size. It lets FFTW optimalize if used with the --benchmark switch. |
| logpower_cf                       | Calculates 10*log10(i^2+q^2)+add_db for the input complex samples. It is useful for drawing power spectrum graphs. |
| encode_ima_adpcm_i16_u8           | Encodes the audio stream to IMA ADPCM, which decreases the size to 25% of the original. |
| decode_ima_adpcm_u8_i16           | Decodes the audio stream from IMA ADPCM. |
| compress_fft_adpcm_f_u8           | Encodes the FFT output vectors of fft_size. It should be used on the data output from logpower_cf. |
| fft_exchange_sides_ff             | It exchanges the first and second part of the FFT vector, to prepare it for the waterfall/spectrum display. It should operate on the data output from logpower_cf. |
| dsb_fc                            | It converts a real signal to a double sideband complex signal centered around DC. |
| add_dcoffset_cc                   | It adds a DC offset to the complex signal: i_output = 0.5 + i_input / 2, q_output = q_input / 2 |
| convert_f_samplerf                | It converts a real signal to the -mRF input format of https://github.com/F5OEO/rpitx, so it allows you to generate frequency modulation. The input signal will be the modulating  |
| fmmod_fc                          | It generates a complex FM modulated output from a real input signal. |
| fixed_amplitude_cc                | It changes the amplitude of every complex input sample to a fixed value. It does not change the phase information of the samples. |
| mono2stereo_s16                   | It doubles every input sample. |
| setbuf                            | See the buffer sizes section. |
| fifo                              | It is similar to clone, but internally it uses a circular buffer. It reads as much as possible from the input. It discards input samples if the input buffer is full. |
| psk31_varicode_encoder_u8_u8      | It encodes ASCII characters into varicode for PSK31 transmission. It puts a 00 sequence between the varicode characters (which acts as a separator). |
| repeat_u8                         | It repeatedly outputs a set of data bytes (given with decimal numbers). |
| uniform_noise_f                   | It outputs uniform white noise. All samples are within the range [-1.0, 1.0]. |
| gaussian_noise_c                  | It outputs Gaussian white noise. All samples are within the unit circle. |
| pack_bits_8to1_u8_u8              | TODO |
| pack_bits_1to8_u8_u8              | It serializes the bytes on the input: it outputs each bit of the input byte as a single byte valued 0x00 or 0x01, starting from the lowest bit and going to the highest bit. |
| awgn_cc                           | It adds white noise with the given SNR to a signal assumed to be of 0 dB power. |
| add_n_zero_samples_at_beginning_f | When the function is executed, it furst writes <n_zero_samples> 32-bit floating point zeros at the output, after that it just clones the input at the output. |
| fft_one_side_ff                   | If the frequency domain signal spans between frequencies -fs/2 to fs/2, this function removes the part from -fs/2 to DC. This can be useful if the FFT of a real signal has been taken (so that the spectrum is mirrored to DC). |
| logaveragepower_cf                | It works like logpower_cf , but it calculates the average of every avgnumber FFTs. |
| mono2stereo_s16                   | It duplicates each 16-bit integer input sample. |
| psk31_varicode_decoder_u8_u8      | It expects symbols encoded as 0x00 and 0x01 bytes on the input, and extracts Varicode characters from them. |
| _fft2octave                       | It is used for plotting FFT data with a GNU Octave session, piping its output to octave -i. |
| invert_u8_u8                      | It maps each 0x00 to 0x01, each 0x01 to 0x00. |
| rtty_baudot2ascii_u8_u8           | This function awaits baudot code characters on its input (ranging from 0b00000000 to 0b00011111), and converts them into ASCII characters. It has an internal state to switch between letters and figures. |
| binary_slicer_f_u8                | If the input sample is below or equals to 0.0, it outputs a 0x00. If the input sample is above 0.0, it outputs a 0x01. |
| serial_line_decoder_f_u8          | It decodes bits from a sampled serial line. It does so by finding the appropriate start and stop bits, and extracts the data bits in between. |
| pll_cc                            | It implements a PLL that can lock onto a sinusoidal input signal. |
| timing_recovery_cc                | It implements non-data aided timing recovery (Gardner and early-late gate algorithms). |
| octave_complex_c                  | It generates octave commands to plot a complex time domain signal. Its output can be piped into octave -i. It plots every samples_to_plot samples out_of_n_samples. |
| psk_modulator_u8_c                | It generates an N-PSK modulated signal from the input symbols. |
| duplicate_samples_ntimes_u8_u8    | It duplicates each sample of sample_size_bytes the given ntimes times. |
| psk31_interpolate_sine_cc         | The input to this function is one complex sample per symbol, the output is interpolation samples per symbol, interpolated using a cosine envelope (which is used for PSK31). |
| differential_encoder_u8_u8        | It can be used while generating e.g. differential BPSK modulation. |
| differential_decoder_u8_u8        | It can be used while demodulating e.g. differential BPSK modulation. The following table show the logic function it performs: |
| bpsk_costas_loop_cc               | It implements a Costas loop for BPSK signals. |
| simple_agc_cc                     | It is an automatic gain control function with a single pole IIR loop filter. |
| peaks_fir_cc                      | It applies a peak filter to the input signal. The peak filter is a very narrow bandpass filter, the opposite of a notch filter. The higher the taps_length is, the sharper the filter frequency transfer function is. |
| firdes_peak_c                     | It designs a FIR peak filter, and writes the taps to the output. More about this filter at peaks_fir_cc. |
normalized_timing_variance_u32_f  | It calculates the normalized timing variance. It works on the sample indexes output from the timing_recovery_cc function. |
| pulse_shaping_filter_cc           | It runs a pulse shaping FIR filter on the signal. |
| firdes_pulse_shaping_filter_f     | It designs a pulse shaping filter, and outputs the taps. It has the same parameters as pulse_shaping_filter_cc. |
| generic_slicer_f_u8               | It decides which symbol the sample corresponds to, where the highest symbol corresponds to 1.0, and the lowest symbol corresponds to -1.0. |
| plain_interpolate_cc              | It interpolates the signal by writing interpolation - 1 zero samples between each input sample. You need to run an anti-aliasing filter on its output. |
| dbpsk_decoder_c_u8                | It implements a differential BPSK demodulator, with the following data flow: |
| bfsk_demod_cf                     | It implements a 2-FSK demodulator, with the following data flow: |
| add_const_cc                      | It adds a constant value of i+q*j to each input sample. |
| pattern_search_u8_u8              | It can be used for preamble search. It looks for a given sequence of N bytes (<pattern_values × N>) in the input data, and if the sequence is found, it reads the following <values_after> bytes and outputs them. The <pattern_values × N> parameter is read as unsigned integers. |
| tee                               | Similarly to the tee command, it reads data from the standard input, and writes it to both a file and the standard output. |

# ToDo

categorise to make it easier to find a command by function
